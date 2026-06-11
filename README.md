# VEYRA — Titanium Series Product Page

A high-end, conversion-focused product page concept for an eyewear e-commerce brand (sunglasses, optical frames, and color contact lenses), built for the GCC market. Designed as a flagship-launch experience in a **light luxe aesthetic** — gallery-white background, bronze-gold accents, ink-black contrast, real photography, an interactive product configurator, and engineering-led storytelling.

**Live demo:** enable GitHub Pages on this repo (see [Deployment](#deployment)) and the page will be live at `https://<username>.github.io/<repo-name>/`

---

## Tech stack

- **Single file** — everything lives in `index.html` (HTML + CSS + vanilla JavaScript)
- **Zero dependencies** — no frameworks, no build step, no package install
- **Fonts** — Syne (display), Inter Tight (body), JetBrains Mono (data/HUD), loaded from Google Fonts
- **Imagery** — placeholder photography served from Unsplash CDN (swap with brand assets for production)

Open the file in any modern browser with an internet connection and it just works.

## Design system

| Token            | Value                | Role                                          |
|------------------|----------------------|-----------------------------------------------|
| `--bg`           | `#faf9f6`            | Gallery-white page background (warm porcelain) |
| `--bg-2`         | `#ffffff`            | Card surfaces                                  |
| `--bg-3`         | `#f1efe9`            | Alternate section background (specs)           |
| `--ink`          | `#16161a`            | Primary buttons, footer, headlines             |
| `--gold`         | `#a8823f`            | Bronze-gold accent: selections, badges, stars  |
| Display type     | Syne                 | Headlines, product names, prices               |
| Body type        | Inter Tight          | Copy, UI labels                                |
| Data type        | JetBrains Mono       | Spec readouts, eyebrows, promo marquee         |

The luxury formula: warm white base + pure white cards + deep gold accents + black power elements (CTAs and footer), with soft diffused shadows instead of hard borders.

## Features

### Hero
- Full-screen photo with a slow zoom-in on page load, fading into the white page from below
- Live "SS26 · Now live" pulse badge
- Engineering stats strip (frame weight, UV400, glare reduction, rating)

### Product configurator
- Photo gallery with crossfade thumbnail switching
- 3D parallax tilt on the main product image (follows the cursor, desktop only)
- Pulsing hotspot markers on the photo that reveal spec callouts (lens coating, hinge, nose bridge)
- Frame finish selector (4 finishes)
- Size selector (S / M / L with frame measurements)
- Lens package selector with live price recalculation:
  - Polarized UV400 — included
  - Polarized + Prescription — +AED 200
  - Photochromic Pro — +AED 350
- Quantity stepper, dynamic Add-to-Bag total, bag counter, toast confirmations

### Conversion layer
- Scrolling promo marquee (B1G1 code, BNPL, click & collect, warranty)
- BNPL line (4 interest-free payments — Tabby / Tamara style)
- Sticky buy bar that slides up after scrolling past the product section
- Virtual try-on buttons with a hook stub for an AR / camera SDK
- Trust signals: ships today, 1-year warranty, 30-day exchange

### Content sections
- Engineering spec grid (6 cards: titanium, polarization, UV400, coating, Rx, hinge durability) on a contrasting ivory band
- Lookbook collection grid with hover zoom and product/price captions
- Verified-buyer reviews with avatars
- Limited-run final CTA and ink-black footer

### Quality floor
- Fully responsive (desktop → tablet → mobile breakpoints at 1020px and 640px)
- Keyboard accessible: focus states, `aria-pressed` selectors, `aria-label`s
- Respects `prefers-reduced-motion` (disables zoom, marquee, parallax, scroll reveals)
- Smooth scroll-reveal animations via IntersectionObserver

## Project structure

```
.
├── index.html      # the entire page: markup, styles, scripts
└── README.md
```

Inside `index.html`, sections are clearly marked with comments:

| Section comment        | What it is                                  |
|------------------------|---------------------------------------------|
| `NAV`                  | Fixed glass navigation with bag counter      |
| `HERO`                 | Full-screen launch hero                      |
| `MARQUEE`              | Scrolling promo strip                        |
| `PRODUCT`              | Gallery + hotspots + configurator panel      |
| `SPECS`                | Engineering spec grid                        |
| `LOOKBOOK`             | Collection grid                              |
| `REVIEWS`              | Social proof                                 |
| `FINAL CTA` / `footer` | Closing conversion block and footer          |
| `stickybar` / `toast`  | Sticky buy bar and notification toast        |

## Deployment

### GitHub Pages (recommended)
1. Push `index.html` and `README.md` to a repository
2. Go to **Settings → Pages**
3. Under **Source**, choose **Deploy from a branch → main → / (root)** and save
4. Your page goes live at `https://<username>.github.io/<repo-name>/` within a minute or two

### Local preview
Just double-click `index.html`, or run a tiny server:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Customization guide

| What                | Where                                                            |
|---------------------|------------------------------------------------------------------|
| Brand name          | `.logo` in the nav and footer (currently "VEYRA")                 |
| Accent color        | `--gold` CSS variable in `:root` (currently `#a8823f`)            |
| Background tone     | `--bg`, `--bg-2`, `--bg-3` variables in `:root`                   |
| Base price          | `const BASE = 899;` in the script + the visible price markup      |
| Lens add-on prices  | `data-add` attributes on `.lens-card` buttons                     |
| Product photos      | `<img src>` URLs in `.main-frame .ph` and `.thumbs`               |
| Hero photo          | `<img>` inside `.hero-img`                                        |
| Hotspot positions   | Inline `top` / `left` styles on `.hotspot` buttons                |
| Copy / spec text    | Plain HTML — edit directly                                        |

## Production notes (for the tech team)

- **Images** are Unsplash placeholders for concept review only. Replace with brand product photography before launch (same `<img>` tags, new URLs or local `/assets` paths). For the light theme, photos with bright, airy backgrounds blend best with the page.
- **Virtual try-on** buttons fire a toast stub (`data-vto`). Wire the click handler to your AR / face-tracking SDK.
- **Add to bag** updates local state only. Connect `addToBag()` to the real cart API / storefront (Shopify, Magento, headless, etc.).
- **Prices, ratings, and review content** are sample data — bind to the product feed.
- No analytics, cookies, or tracking included — add per your stack.

## License & attribution

Internal concept build for design review — not affiliated with any existing retailer. Placeholder images are served from [Unsplash](https://unsplash.com) under the Unsplash License; replace before any commercial launch. Fonts via [Google Fonts](https://fonts.google.com) (open source licenses).
