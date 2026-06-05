# PM Vectors — Website

Marketing site for **PM Vectors**, a Pune-based licensed electrical contractor backed by in-house RCC precast manufacturing.

- **Domain:** pmvectors.com
- **Contact:** +91 77700 55835 · contact@pmvectors.com
- **Factory:** Waki, Baramati, Pune Dist., Maharashtra

## What's in the site

| Page | Purpose |
|---|---|
| `index.html` | Home — hero, about, two-division split (Electrical primary, RCC secondary), products, electrical services, project gallery, why us, testimonials, contact form |
| `resources.html` | Downloadable engineering references — DSR rate cards, MERC/MSEDCL circulars, technical references, BOQ + estimation tools |
| `gallery.html` | Photo gallery of on-site work — JSON-driven, filterable by Electrical / RCC |

## Tech stack

Single-file static site. No build step.

- **HTML + Tailwind CSS via CDN** (`cdn.tailwindcss.com`)
- **Vanilla JS** for nav dropdowns, mobile menu, form submission, gallery filter, counters
- **AOS** for scroll-triggered animations
- **Google Fonts:** Space Grotesk (display), Manrope (body), Bebas Neue (impact stats), JetBrains Mono (monospace accents)
- **Web3Forms** for the contact form (key embedded in `index.html`)

## Project structure

```
pm-vectors/
├── index.html              Home page
├── resources.html          Downloads page (14 documents)
├── gallery.html            Photo gallery (manifest-driven)
├── assets/
│   ├── logo/
│   │   └── pm-vectors-logo.jpg
│   ├── docs/               14 downloadable PDFs + 1 XLSX
│   └── photos/
│       ├── photos.json     Gallery manifest
│       └── *.jpg           Site photos (21 currently)
└── .gitignore
```

## Running locally

The gallery loads `photos.json` via `fetch()`, which is blocked over `file://`. Use any local web server:

```bash
# Python
python3 -m http.server 4747

# Or Node (if you have it)
npx serve .
```

Then open <http://localhost:4747>.

Once deployed to a real domain (Netlify / Vercel / Cloudflare Pages / any static host) it just works — no configuration needed.

## How to add photos to the gallery

1. Drop the image into `assets/photos/` (JPG, PNG or WebP)
2. Open `assets/photos/photos.json` and add an entry to the `photos` array:

```json
{
  "file": "substation-pune-2026.jpg",
  "caption": "DTC Substation Erection",
  "location": "Pune, MH",
  "category": "electrical"
}
```

- `category` must be `"electrical"` or `"rcc"`
- `location` is optional
- Order in the array determines order in the masonry grid

Refresh the page — the photo appears immediately.

## How to add a document to Resources

1. Drop the file into `assets/docs/` (PDF, XLSX)
2. Add a card to the appropriate category in `resources.html` — copy any existing `<a class="doc-card …">` block and update the file path, title, description, badge, file size

## Navigation structure

Each page shares a consistent nav with two dropdowns:

- **Divisions ▾** → Electrical Services · RCC Precast
- **Resources ▾** → Downloads · Photo Gallery

Mobile uses a hamburger that expands the same items grouped under DIVISIONS / RESOURCES labels.

## Brand notes

- **Positioning:** "Powered Connections. Strong Foundations." — Electrical is the primary division, RCC precast is the in-house supporting capability
- **Capacity line:** "10 MVA · Transformer capacity handled"
- **Accents:** Amber/rebar (`#F59E0B`) for Electrical, concrete grey for RCC, deep ink (`#070A14`) base palette

## License

Proprietary — © 2026 PM Vectors. Website by BytePhase Web Services.
