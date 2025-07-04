# STAGE 1: Build a custom Caddy with the Cloudflare plugin
FROM caddy:2-builder AS builder

RUN xcaddy build \
    --with github.com/caddyserver/dns.providers.cloudflare

# STAGE 2: Create the final, small production image
FROM caddy:2-alpine

# Copy the custom-built Caddy binary from the builder stage
COPY --from=builder /usr/bin/caddy /usr/bin/caddy

# Copy our Caddyfile
COPY Caddyfile /etc/caddy/Caddyfile
