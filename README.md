# Tech Surge — Netlify storage edition

This package replaces the Supabase setup in the original single-file Tech Surge site with Netlify Blobs and a Netlify Function. Public visitors can read published stories; drafts are returned only when the private admin password is supplied.

## Free-tier note
Netlify has a free plan with monthly usage limits. This project does not require Supabase or a paid database, but it is not unlimited. Check your Netlify usage if traffic grows.

## Deploy to the existing Netlify site
Because Netlify must build and deploy the server function, this needs a Git-connected deployment (a simple drag-and-drop static deploy will not deploy the function).

1. Create a GitHub repository for this folder and upload the files/folders exactly as shown (`public`, `netlify`, `netlify.toml`, `package.json`).
2. In Netlify, open your existing Tech Surge site and connect it to that GitHub repository using **Project configuration / Build & deploy / Continuous deployment**.
3. Build command: `npm run build`; publish directory: `public`. The included `netlify.toml` already defines these.
4. In the Netlify site dashboard, open **Environment variables** and add `TECH_SURGE_ADMIN_PASSWORD` with a new strong password. Do not put this password in the HTML file or share it with anyone.
5. Trigger a new deploy.
6. Open your website, click **Admin**, and sign in with that password.

## Notes
- Articles, pages, navigation, categories and site settings are stored in Netlify Blobs and sync across devices.
- The initial content can be seeded by signing in on the first deployment and saving the current content. The included sample stories are demo content; remove them if you do not want them public.
- The existing editor stores cover images as image URLs. This project does not upload image files directly to cloud storage.
- Do not place secrets in `public/index.html`.
