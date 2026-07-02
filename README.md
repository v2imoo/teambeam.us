# TeamBeam Outings USA — teambeam.us

Static marketing site for **TeamBeam Outings USA**. 137 self-contained HTML pages, fully
optimized for search engines, AI answer engines (ChatGPT, Claude, Gemini, Perplexity, Copilot),
mobile devices, and social sharing. Built to deploy on **Cloudflare Pages** from **GitHub** with
zero build step.

> **Designed. Delivered. Measured.** · People · Teams · Organisations · Beyond.

---

## What's in this repo

| Type | Files |
|---|---|
| Pages | 136 content pages + `404.html` (all flat, at the repo root) |
| Landing splitter | `go.html` → served at `/go` (US ↔ India chooser) |
| Interactive tools | `resources-tools-*.html` (idea generator, ROI calculator, team-health snapshot, flight-hub finder) — all client-side, **no email/inputs collected** |
| SEO / crawlers | `robots.txt`, `sitemap.xml` (136 URLs) |
| Social / rich cards | Open Graph + Twitter tags + JSON-LD structured data on every page |
| PWA / icons | `site.webmanifest`, `favicon.svg`, `favicon.ico`, `icon-180/192/512.png`, `og-cover.png` |
| Cloudflare config | `_headers` (security + caching), `_redirects` (clean URLs + aliases) |

No frameworks, no build, no dependencies. Every page is plain HTML/CSS/JS.

---

## Deploy to Cloudflare Pages via GitHub (5 minutes)

### 1. Put this folder in a GitHub repo
```bash
cd teambeam-us-site
git init
git add .
git commit -m "TeamBeam US site"
git branch -M main
git remote add origin https://github.com/<your-username>/teambeam-us.git
git push -u origin main
```
(Or drag-and-drop the files into a new repo on github.com.)

### 2. Connect it in Cloudflare
1. Cloudflare dashboard → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
2. Pick your `teambeam-us` repo.
3. Build settings:
   - **Framework preset:** `None`
   - **Build command:** *(leave empty)*
   - **Build output directory:** `/`  *(the repo root — files are already built)*
4. **Save and Deploy.** You'll get a `*.pages.dev` URL immediately.

### 3. Point teambeam.us at it
1. In the Pages project → **Custom domains** → **Set up a custom domain** → enter `teambeam.us`.
2. If your DNS is on Cloudflare, records are added automatically. Add `www` too and it will
   redirect to the apex.
3. HTTPS is automatic. Done.

Every `git push` to `main` redeploys automatically.

---

## After you go live — quick checklist

- [ ] **Google Forms:** open `contact.html` and paste your live form URLs into the `FORMS{}`
      block near the bottom (until then each path falls back to the correct `mailto:`).
      Same optional slots exist on `resources-insights.html` (newsletter) and
      `resources-podcast.html` (platform links).
- [ ] **Social handles:** the footer links to `linkedin.com/company/teambeam`,
      `instagram.com/teambeamoutings`, `x.com/teambeamoutings`, `youtube.com/@teambeamoutings`,
      `facebook.com/teambeamoutings`. **Confirm/replace** these with your real handles
      (search `teambeamoutings` across the repo). They're also listed in every page's JSON-LD
      `sameAs` and in the `twitter:site` tag.
- [ ] **Search Console + Bing:** verify the domain and submit `https://teambeam.us/sitemap.xml`.
- [ ] **Social preview:** the share image is `og-cover.png` (1200×630). Replace it with a
      designed version anytime — keep the filename and it flows to every page automatically.

---

## SEO / AI-crawler notes

- **`robots.txt` explicitly welcomes** Googlebot, Bingbot, Applebot, plus the AI answer-engine
  crawlers — GPTBot, OAI-SearchBot, ChatGPT-User, ClaudeBot, anthropic-ai, PerplexityBot,
  Google-Extended, Amazonbot, Meta-ExternalAgent, cohere-ai, and more — so the site can be
  indexed **and cited** by ChatGPT, Claude, Gemini, Perplexity and Copilot.
- **Structured data (JSON-LD)** on every page: `Organization`, `WebSite`, `WebPage`,
  `BreadcrumbList`, plus `LocalBusiness` (with geo + Google Maps) on home/contact/landing.
- **Clean URLs:** links have no `.html`; `_redirects` 301s any legacy `.html` request to the
  clean path, and `sitemap.xml` lists the canonical clean URLs.
- **Per-page** canonical, Open Graph, Twitter Card, theme-color, geo tags, and manifest.

## Local preview
```bash
cd teambeam-us-site
python3 -m http.server 8080
# visit http://localhost:8080  (clean URLs resolve on Cloudflare; locally use /index.html etc.)
```

## Contact
TeamBeam Outings USA · 600 California St, 11th Floor, San Francisco, CA 94108
start@teambeam.us · +1 (415) 404-9200 · teambeam.us · sister home: teambeam.in
