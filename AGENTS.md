# Base44 Dev Environment

## Project Overview
Static HTML website for a personal SMS messaging service. No build system, no backend, no dependencies — just plain HTML files and one PNG image.

## How It Runs
- Served by **nginx:alpine** via `docker-compose.base44.yml`, bind-mounting the repo root at `/usr/share/nginx/html`.
- A custom `nginx.base44.conf` runs nginx as `root` because the sandbox repo directory has restrictive (700) permissions that the default nginx worker user cannot traverse.
- Web entry point is **port 3000** (mapped to nginx's port 80).
- No live-reload dev server (static files). After editing HTML, call `reload_preview` to see changes in the preview.

## Verification
- `curl -s -o /dev/null -w "%{http_code}" http://localhost:3000/index.html` should return 200.
- All pages: index, about, contact, privacy, terms, verbal-optin, optin.

## Secrets
None required. No external services.
