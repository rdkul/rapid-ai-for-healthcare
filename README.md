# Rapid AI for Healthcare — Portfolio Site

The personal portfolio site for *Rapid AI for Healthcare*. Built with [Astro](https://astro.build/) (a fast static-site framework). Deploy to [Vercel](https://vercel.com/) (free tier).

---

## What's in here

```
.
├── astro.config.mjs        # Astro config (update the `site` URL when you have a domain)
├── package.json            # Dependencies
├── public/                 # Static assets (favicon, images, downloadable engine files like pov-engine.md, dd-engine.md)
│   └── favicon.svg
├── src/
│   ├── components/         # Reusable Astro components
│   │   └── WorkflowCard.astro
│   ├── layouts/            # Page wrappers (header, footer, fonts)
│   │   └── BaseLayout.astro
│   ├── pages/              # Each file = one URL route
│   │   ├── index.astro     # /  (home)
│   │   ├── about.astro     # /about
│   │   └── workflows/
│   │       ├── index.astro            # /workflows
│   │       └── rapid-pov-engine.astro # /workflows/rapid-pov-engine
│   └── styles/
│       └── global.css      # All the styling lives here
└── README.md
```

**Adding a new workflow page later** = create one new file at `src/pages/workflows/[your-workflow].astro` and add a `<WorkflowCard>` to the home and workflows index pages. The site will auto-route it. No build config to touch.

---

## Run locally

You'll need [Node.js 20+](https://nodejs.org/) installed.

```bash
# Install dependencies
npm install

# Start the dev server
npm run dev
# → site running at http://localhost:4321
```

The dev server hot-reloads on every save.

To build a production bundle:

```bash
npm run build
# → static files generated to dist/

npm run preview
# → preview the production build locally
```

---

## Deploy to Vercel (recommended)

The site is a static Astro build, which Vercel deploys natively in seconds. Two paths:

### Path A — Connect via GitHub (recommended)

1. **Create a GitHub account** if you don't have one: [github.com/signup](https://github.com/signup)
2. **Create a new repository** at [github.com/new](https://github.com/new). Name it whatever you want (e.g. `rapid-ai-for-healthcare`). Make it public or private — Vercel works with both.
3. **Upload these files** to the repo:
   - The simplest way: in your new repo, click "uploading an existing file" and drag every file in this folder. Then commit.
   - The technical way: install Git, run `git init`, `git remote add origin [your repo URL]`, `git add .`, `git commit -m "initial site"`, `git push -u origin main`.
4. **Sign up at [vercel.com](https://vercel.com/)** with your GitHub account.
5. **Click "Add New Project"** → select your new repo → Vercel auto-detects Astro and deploys.
6. **Done.** Site is live at `your-repo.vercel.app` in ~30 seconds.

After this, **every change you push to GitHub auto-deploys to Vercel within a minute**. No manual deploy step.

### Path B — Direct upload

1. Run `npm run build` locally — generates a `dist/` folder.
2. Sign up at [vercel.com](https://vercel.com/).
3. Use the Vercel CLI (`npm i -g vercel` then `vercel` in the project root) — follow the prompts.

Path A is much better for ongoing updates; this is for a one-shot deploy.

---

## Custom domain (optional)

1. Buy a domain from [Cloudflare](https://www.cloudflare.com/products/registrar/), [Namecheap](https://www.namecheap.com/), or [Porkbun](https://porkbun.com/) (~$10–15/year). Cloudflare is cheapest if you transfer for the renewal.
2. In Vercel → your project → Settings → Domains → add your domain.
3. Vercel walks you through the DNS records to add at your registrar. ~10 minutes end to end.
4. Update the `site` URL in `astro.config.mjs` to match your custom domain.

Suggested domain ideas if `rapid-ai.health` or similar is taken: `your-name.com`, `rapidai.dev`, `rapidai.commercial`, `rapid-ai-for-healthcare.com`.

---

## Adding a new workflow page

1. Create `src/pages/workflows/[your-workflow-slug].astro`. Use `rapid-pov-engine.astro` as a template — copy it and edit the content.
2. In `src/pages/index.astro`, add a `<WorkflowCard>` for the new workflow under "Currently live" (or the appropriate section).
3. In `src/pages/workflows/index.astro`, add a `<WorkflowCard>` for the new workflow.
4. Commit and push. Vercel auto-deploys.

You can edit any file directly in GitHub's web UI (no command line needed) — open the file, click the pencil icon, paste new content, commit. Vercel rebuilds within a minute.

---

## Editing copy

All text content lives in the `.astro` files in `src/pages/`. They're just HTML with a frontmatter section at the top. Edit the text between the tags, save, refresh.

The hero headline lives in `src/pages/index.astro` — search for `I build` to find it.

---

## Theming

All design tokens (colors, fonts, spacing) live as CSS variables at the top of `src/styles/global.css`. To change the accent color from lime to (say) cyan, change the `--accent` value in one place and it cascades site-wide.

---

## Things to fill in before going live

A grep through the codebase for placeholders to replace:

- [ ] `mailto:raulkulkarni@gmail.com` in `BaseLayout.astro` — your real email
- [ ] LinkedIn URL in `BaseLayout.astro` footer — your real LinkedIn profile
- [ ] GitHub URL in `BaseLayout.astro` footer — your GitHub profile or remove
- [ ] GitHub repo URL in `rapid-pov-engine.astro` ("Get the engine on GitHub →") — link to your published engine repo
- [ ] `site` URL in `astro.config.mjs` — your final domain
- [ ] Footer copyright year ("2026") — current year, optionally your name
- [ ] Brand text in header (`/ rapid ai for healthcare`) — keep or customize

---

## Recommended next moves after launch

1. Push the site live (Vercel) on a free `*.vercel.app` URL first. Don't wait for the perfect domain.
2. Buy a custom domain and connect it (10 minutes).
3. Write the LinkedIn announcement post. Link the live site.
4. DM 15–25 specific people who'd care — the post is the broadcast, the DMs are the signal.
5. Start the next workflow build. The site rewards consistent shipping.
