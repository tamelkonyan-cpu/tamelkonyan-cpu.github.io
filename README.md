# Personal site — setup notes

Plain HTML and CSS. No Jekyll, no build step, no dependencies. Edit the files
directly on GitHub if you like; changes go live in under a minute.

---

## Files

| File | What it is |
|---|---|
| `index.html` | Home / About. Also holds the JSON-LD block that ties your identity together for Google. |
| `publications.html` | All 48 journal articles, generated from your existing list. |
| `research.html` | Research themes + a working-papers section (currently a placeholder). |
| `teaching.html` | Courses. |
| `404.html` | Shown for bad URLs. GitHub Pages picks this up automatically. |
| `style.css` | All styling. Change a colour or font here and it applies everywhere. |
| `robots.txt`, `sitemap.xml` | For search engines. |

Two files you need to add yourself:

- **`photo.jpg`** — your headshot. Save the one from your Wix site (right-click →
  Save image as). Roughly 600 × 700 px is plenty. If it's missing, the page still
  works; the photo block just disappears.
- **`cv.pdf`** — your CV. Every "CV" link points here.

---

## Publishing it

1. Create a free account at **github.com** if you don't have one.
2. Create a **new public repository** named exactly `YOURUSERNAME.github.io`
   (substitute your actual GitHub username). Tick "Add a README file" — you'll
   overwrite it.
3. On the repo page: **Add file → Upload files**. Drag in everything from this
   folder, plus `photo.jpg` and `cv.pdf`. Commit.
4. **Settings → Pages**. Under *Source*, choose *Deploy from a branch*, branch
   `main`, folder `/ (root)`. Save.
5. Wait about a minute. The site is live at `https://YOURUSERNAME.github.io`.

Every later edit is: open the file on GitHub, click the pencil icon, change it,
commit. The site updates itself.

---

## Putting your own domain on it

GitHub Pages hosts custom domains for free — you only pay the registrar for the
name itself, typically $12–15 a year at Namecheap, Cloudflare or Porkbun.

1. Buy `tigranmelkonyan.com` (or `.net` / `.org`).
2. At the registrar's DNS settings, add four **A records** for the bare domain,
   all pointing at GitHub:

   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```

   Then one **CNAME record**, host `www`, pointing to `YOURUSERNAME.github.io`.
   (Check GitHub's current values at
   docs.github.com → Pages → *Managing a custom domain* — they change rarely
   but do change.)
3. Back on GitHub: **Settings → Pages → Custom domain**, enter
   `tigranmelkonyan.com`, save. This writes a `CNAME` file into the repo.
4. DNS takes anywhere from ten minutes to a day. Once GitHub shows a green
   check, tick **Enforce HTTPS**.

---

## Find-and-replace before you go live

Every page has `https://tigranmelkonyan.com` hard-coded in its `canonical` tag,
and the same appears in `robots.txt`, `sitemap.xml`, and the JSON-LD block in
`index.html`. Replace all of them with whatever domain you end up on
(`YOURUSERNAME.github.io` works fine as an interim value).

Getting these right matters: the canonical tag tells Google which URL is the
real one, and the JSON-LD `sameAs` list is what tells it that this site, your
Culverhouse page, your Scholar profile and your RePEc profile are all the same
person.

---

## After it's live

1. **Google Search Console** (search.google.com/search-console) — add the site,
   verify by DNS or by uploading the HTML file it gives you, then submit
   `sitemap.xml`. Do the same at **Bing Webmaster Tools**.
2. **Retire the Wix site**, or at minimum put a single line on it linking here,
   so the two aren't competing for the same searches.
3. **Collect the links.** Add the new URL to your Google Scholar homepage field,
   your RePEc author profile, ORCID, SSRN, ResearchGate, LinkedIn, Academia.edu,
   and your email signature. Ask Culverhouse communications to add a "Personal
   website" link to your faculty page — that one is worth more than all the
   others put together.

---

## Editing notes

- Sections marked `<!-- EDIT ME -->` are drafts or placeholders.
- To add a publication, copy an existing `<li>` block in `publications.html` and
  change the year, title, link and journal line.
- The hairline-with-end-ticks rule under your name and above each section is a
  single CSS class, `.interval`. Add `<div class="interval"></div>` anywhere you
  want one.
- Colours and typefaces are all defined once at the top of `style.css`, in the
  `:root` block.
