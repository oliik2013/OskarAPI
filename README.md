# Random Cat API (Cloudflare Worker)

This repo is a random cat image API deployed to **Cloudflare Workers** (via GitHub Actions).

## Why this works better than GitHub Pages for Discord

GitHub Pages is static, so true per-request random image responses are limited.
A Worker can choose a random image on every request, so each refresh can return a new cat.

## Endpoints

- `/raw` → responds with a random image file directly (no client-side redirect).
- `/random` → minimal HTML containing only an `<img>` plus OpenGraph/Twitter image tags for embeds.
- `/img/<filename>` → serves a specific image from `pics/`.

## Add images

1. Put files in `pics/` (`.jpg`, `.jpeg`, `.png`, `.gif`, `.webp`, `.avif`).
2. Push to `main`.
3. GitHub Action deploys Worker and regenerates image manifests.

## Required GitHub secrets

Set these in your repo:

- `CLOUDFLARE_API_TOKEN`
- `CLOUDFLARE_ACCOUNT_ID`

## Local manifest generation

```bash
node scripts/generate-image-list.mjs
```
