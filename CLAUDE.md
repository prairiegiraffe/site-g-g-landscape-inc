# G&G Landscape, Inc. — Professional Site Build

## Quick Start
1. Read this file completely before building
2. The shell CSS is at `css/styles.css` — it defines the full design system
3. Section templates are in `sections/` — use them as starting patterns
4. Build each page as a standalone `.html` file in the root directory
5. Run `npx serve .` to preview locally
6. When done, `git add . && git commit -m "Build site" && git push` to deploy

## Business Facts (DO NOT INVENT — write around missing info)

| Field | Value |
|-------|-------|
| **Business Name** | G&G Landscape, Inc. |
| **Industry** | Landscaping |
| **Type** |  |
| **Tagline** | N/A |
| **Years in Business** | N/A |
| **Phone** | (307) 682-9900 |
| **Email** | office@gglandscapeinc.com |
| **Address** | 5400 Hitt Boulevard, Gillette, WY |
| **Primary Location** | Gillette |
| **Personality** | Direct, confident, professional |
| **Target Audience** | Large Business/Contractor/City/Large Residential |
| **Inspiration Sites** | PRC |

### About
Commercial/Residential Landscaping

### Services (12 total)
1. Commercial-Site Grading & Prep
2. Irrigation Systems
3. Landscape Installation
4. Retaining Walls
5. Hardscapes
6. Artificial Turf Installation
7. Sod & Lawn Installation
8. Hydroseeding
9. Tree Planting
10. Drainage/Erosion Control
11. Paver Patios & Walkways
12. Water Features & Ponds

### Service Areas
- Gillette (primary)
- Sheridan
- Buffalo
- Casper
- Douglas
- Sundance
- Spearfish

## Design System

**Shell**: `service_business`
**Fonts**: Figtree (headings) + Inter (body)
**Brand Color**: Forest Green, White & Black

The shell CSS (`css/styles.css`) defines all design tokens as CSS custom properties:
```
--color-primary: #1f4d2b;
  --color-primary-dark: #102917;
  --color-primary-light: #60bf78;
  --color-primary-tint: rgba(31, 77, 43, 0.08);
  --color-primary-tint-strong: rgba(31, 77, 43, 0.18);
  --color-accent: #247561;
  --color-dark: #0f172a;
  --color-muted: #4b5563;
  --color-border: #e5e7eb;
  --color-surface: #f9fafb;
  --color-surface-alt: #f3f4f6;
  --color-on-primary: #ffffff;
  --font-heading: "Figtree", system-ui, -apple-system, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  --font-body: "Inter", system-ui, -apple-system, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  --container: 1200px;
  --container-narrow: 800px;
  --radius-sm: 6px;
  --radius: 12px;
  --radius-lg: 20px;
  --shadow-xs: 0 1px 2px rgba(15, 23, 42, 0.05);
  --shadow-sm: 0 2px 8px rgba(15, 23, 42, 0.06);
  --shadow-md: 0 8px 24px rgba(15, 23, 42, 0.08);
  --shadow-lg: 0 20px 40px rgba(15, 23, 42, 0.12);
  --shadow-primary: 0 10px 40px -10px var(--color-primary-tint-strong);
  --transition: 0.22s cubic-bezier(0.2, 0.8, 0.2, 1);
```

### Key CSS Classes
- `.container` — max-width centered container
- `.container-narrow` — narrower container for text-heavy sections
- `.eyebrow` — small uppercase label with accent bar (used above section headings)
- `.btn`, `.btn--outline`, `.btn--inverse`, `.btn--ghost` — button variants
- `.hero` — full-bleed hero with `.hero__bg` background image
- `.stats` — stat strip with `.stat`, `.stat__value`, `.stat__label`
- `.service-grid` + `.service-card` — card grid for services
- `.feature-row` + `.feature-row.reverse` — alternating image/text rows
- `.diff-grid` + `.diff-card` — icon cards for differentiators/values
- `.process-list` — numbered timeline
- `.faq` — accordion using `<details>`/`<summary>`
- `.project-grid` + `.project-card` — photo cards with metadata
- `.testimonial` — two-column quote + photo
- `.contact-grid` + `.contact-form` — form + contact info card
- `.cta-section` — dark call-to-action banner
- `.site-header` — sticky dark header
- `.site-footer` — dark footer with grid columns
- `.page-section`, `.page-section.alt`, `.page-section.dark` — section wrappers

## Pages to Build

Build these as standalone HTML files. Each file should be a complete document
(`<!DOCTYPE html>` through `</html>`) that links to `css/styles.css`.

1. **index.html** (Home) — Hero, stats strip, services overview, featured capabilities with photos, about teaser, service areas, CTA
2. **about.html** — Company story, team/leadership (if info available), values/differentiators, CTA
3. **services.html** — All services as card grid with icons
4. **services/[slug].html** — One per service: hero, overview, what-we-do, process timeline, FAQ, CTA
5. **contact.html** — Contact form + info card + map, company field for B2B
6. **service-areas.html** — Area cards grid (if multiple areas)

### Page Structure Rules
- **ALL internal links must use RELATIVE paths** — never use `/api/projects/` URLs
  - From root pages: `href="services/hardscapes.html"` or `href="about.html"`
  - From service pages: `href="../about.html"` or `href="../contact.html"`
  - CSS from root: `href="css/styles.css"` — from subdirectories: `href="../css/styles.css"`
  - The `/api/projects/.../serve/` URLs are for the platform editor only, NEVER in page HTML
- Every `<section>` needs `data-block-id="page:section-name"` (for the platform editor)
- Editable text slots get `data-content="slot-name"` attributes
- Contact form needs `data-devtools-form` and `data-form-type="contact"`
- Header wraps in `data-devtools-partial="header"`
- Footer wraps in `data-devtools-partial="footer"`
- Hero images: `loading="eager" fetchpriority="high"`
- All other images: `loading="lazy"`
- H1 → H2 → H3 hierarchy, no skips
- Meta description on every page, ≤ 155 chars
- Include LocalBusiness schema JSON-LD on home page

## Section Templates

The `sections/` directory contains HTML section templates you can reference.
These are from the oatmeal-olive-mona and Studio template libraries — adapt
the structure and layout patterns but use the shell's CSS classes, not Tailwind.

Available sections:
- `stats-four-columns.html` — grid of stat cards
- `features-alternating.html` — alternating image/text feature rows
- `features-three-column.html` — three-column feature cards
- `testimonial-large-photo.html` — quote + large photo side by side
- `team-grid.html` — team member photo grid
- `faqs-accordion.html` — two-column FAQ with accordion
- `hero-with-photo.html` — hero with side photo
- `cta-simple.html` — centered call-to-action

## Copy Writing Rules

1. **Never invent facts.** If a specific fact is missing (founding year, certifications, team size), rewrite the sentence so it doesn't need that fact. Don't use placeholder markers.
2. **No slop.** Avoid: "in today's world", "look no further", "state-of-the-art", "one-stop shop", "world-class", "industry-leading", "leverage", "synergies", "cutting-edge", "seamless", "pristine", "unlock the potential", "game-changer", "delve into", "tapestry of", "plethora of", "myriad of".
3. **No self-congratulation.** Skip "We're proud to...", "We take pride in...", "Our commitment to...".
4. **Be direct.** Write what the business does, not what it "may help" with.
5. **Use the business name** at least once per page, not "our company".
6. **Mention specific services and areas by name** — pull from the facts above.
7. **Match the personality** — direct, confident, plain-spoken, professional.
8. **B2B tone** — speak to project managers, procurement, field supervisors. Not homeowners.

## Images

### AI Image Generation (preferred)
Generate images on demand using the platform API. Each call creates a photorealistic
image via AI, saves it to R2, and returns a URL you can use directly in `<img src>`.

```bash
curl -X POST "https://devtools.prairiegiraffe.com/api/projects/proj_80x27mqq/sites/49/generate-image" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer dtk_27625d1c6a10c7c6a9c688ab356421f2f16fe9b26f40869a92cbf3ec41d50661" \
  -d '{
    "prompt": "Heavy equipment excavator on an oilfield pad construction site, Wyoming prairie, golden hour",
    "filename": "hero-excavation",
    "aspect": "landscape"
  }'
# Returns: { "success": true, "url": "/api/projects/.../serve/assets/hero-excavation-a1b2c3d4.webp", ... }
```

**The token above is pre-filled and valid for 30 days.** No additional auth setup needed.

**Parameters:**
- `prompt` (required) — Describe the image. Be specific about subject, setting, lighting.
- `filename` (optional) — Stem for the filename. Default: "image". Use descriptive names like "hero-main", "about-team", "service-fencing".
- `aspect` (optional) — "landscape" (1536x1024), "portrait" (1024x1536), or "square" (1024x1024). Default: "landscape".

**Cost:** ~$0.05 per image. Generate only what you need.

**The URL returned is a relative path** — use it directly as the `src` attribute:
```html
<img src="/api/projects/proj_80x27mqq/sites/49/serve/assets/hero-excavation-a1b2c3d4.webp"
     alt="Excavation work in Wyoming" loading="eager" />
```

### Unsplash Fallback
If you can't generate (no session cookie, API down), use Unsplash:
```
https://source.unsplash.com/1600x900/?Landscaping,work
https://source.unsplash.com/800x1000/?Landscaping,team
```

### Client Uploads
When the client provides real photos later, they'll be uploaded at:
`https://devtools.prairiegiraffe.com/api/files/sites/proj_80x27mqq/1776201835363/assets/[filename]`

## Deployment

- **Repo**: https://github.com/prairiegiraffe/site-g-g-landscape-inc
- **Live URL**: https://site-g-g-landscape-inc.pages.dev
- Push to `main` branch → auto-deploys via Cloudflare Pages
- No build step — CF Pages serves static files directly

## Platform Integration

This site is tracked in the devtools platform as a `captured_sites` row.
After building, the owner can:
- Edit pages visually in the platform editor
- Run SEO audits
- Generate fulfillment plans
- Share with clients for review
