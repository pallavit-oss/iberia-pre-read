# Headout · Iberia Role Pre-Read Page

A candidate-facing pre-read page built for Headout's Business Development Manager, Iberia role, based in Madrid. Designed to be shared by the recruiter before the first call, giving candidates a real sense of the role, the team, and the interview process before they speak.

Built as a single, self-contained HTML file with no external dependencies at runtime — all fonts and icons are embedded inline.

This page was adapted from the [Italy pre-read](https://github.com/pallavit-oss/italy-pre-read), reusing the same design system, layout, and structure with Iberia-specific content.

---

## What This Is

A bespoke recruitment micro-site replacing the standard PDF or LinkedIn job description. The goal is to give candidates something closer to a product experience — informative, personal, and reflective of Headout's brand — rather than a wall of text.

The page was designed and iterated entirely through AI-assisted development using Claude (Anthropic), with all copy, structure, layout, and code produced and refined through conversation.

---

## Page Structure

The page is a single scrollable document with six sections, accessible via a fixed navigation bar:

| Section | ID | Description |
|---|---|---|
| The Role | `#role` | Four pillars explaining what the role involves |
| The Opportunity | `#market` | Spain/Portugal market context, opportunity, and growth path |
| Culture | `#values` | Headout's six operating principles in a scrollable carousel |
| The Team | `#team` | Video slide featuring the hiring manager |
| Interview | `#process` | Six-step interview process with timeline and prep guidance |
| FAQs | `#faq` | Six accordion questions with a contextual aside card |

---

## Iberia-Specific Content

- **Role:** Business Development Manager, Iberia — based in Madrid (exact office address TBC)
- **Reports to:** Diego Valera, GM · Iberia & South America
- **Skip-level:** Vlad Grankin, GM · Europe & LATAM
- **Team:** 5 Business Development Managers, 2 Business Growth Managers, and 5+ central team members dedicated to the Iberian market
- **Market focus:** Spain and Portugal (Sagrada Família, Park Güell, Alhambra, Royal Palace of Madrid, Santiago Bernabéu Tours, Seville Cathedral, Alcázar of Seville, Pena Palace, Jerónimos Monastery, Oceanário Lisboa, Ibiza nightlife)
- **Languages:** Portuguese and English
- **Interview process:** Recruiter Connect → Case Study (Iberia-adapted) → call with Diego Valera → GM Europe & LATAM (Vlad Grankin) → Reference Check → Offer

### TODO before sharing with candidates

- ~~**Fonts:** an earlier draft used Google Fonts (Plus Jakarta Sans + Inter) instead of Headout's licensed Halyard Display/Halyard Text.~~ Fixed — the licensed Halyard fonts (same base64-embedded OTFs as the Italy/France repos) are now embedded directly, matching those pages exactly.
- **Office address:** the hero card, location card, and Google Maps embed currently point at a generic "Madrid, Spain" pin. Replace with the exact office address once confirmed (search `TBC` in `index.html`).
- **Team video:** the Team section shows a "Video coming soon" placeholder for Diego Valera, with a purple initials tile (`DV`) instead of a photo. To add a Loom video, find `video-slide-player` in `index.html` (search `VIDEO TODO` is not present — look for `video-placeholder` inside `#vslide-0`) and replace it with:
  ```html
  <iframe
    src="https://www.loom.com/embed/YOUR_VIDEO_ID?hide_owner=true&hide_share=true&hide_title=true&hideEmbedTopBar=true"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="width:100%;height:100%;border-radius:16px;display:block;"
  ></iframe>
  ```
  Replace the `vsb-avatar` initials tile with a `vsb-avatar-img` (base64-encoded photo) when available. If a second team member (e.g. a peer BDM) records a video, duplicate the slide structure and restore the video-carousel JS/nav removed in this version (see git history of the Italy/France repos for the two-slide pattern).
- **Top experiences:** the tag cloud currently lists attraction names as plain (non-linked) chips, since exact Headout product-page URLs for Spain/Portugal weren't available when this was built. Add real `https://www.headout.com/...` links once known (see how the Italy/France repos link theirs).
- **OG image:** no social-preview image is wired up yet (the Italy repo uses a Colosseum photo; this repo has none). Add an `og-image.jpg` (1200×630) and restore the `og:image`/`twitter:image` meta tags in `<head>` once you have one — e.g. a Madrid/Barcelona/Lisbon landmark shot.
- **"Explore more on Headout" partnership highlight:** the France repo names a specific recent partnership win in the Opportunity section (Bertrand Hospitality × Versailles). Add an Iberia-equivalent highlight if there's one worth featuring.

---

## Features

### Design & Layout
- Fully responsive across desktop, tablet, and mobile (breakpoints at 768px and 1024px)
- Fixed navigation header with hamburger menu on mobile
- Hero section with stat counters and three contextual info cards
- Custom colour system using CSS variables throughout

### Typography
- **Halyard Display** — headings, section titles, hero text, and nav
- **Halyard Text** — body copy, labels, and captions
- Both font families embedded as base64-encoded OTF files via `@font-face`, removing any dependency on external font hosting

### Technical Details
- **Single file** — all CSS, JS, fonts, and content in one `index.html`
- **No external dependencies at runtime** — no CDN calls, no Google Fonts, no external scripts (Loom embeds are the exception once a video is added)
- **Responsive** media queries across all sections
- **Intersection Observer** for scroll-triggered fade-in animations
- The Spain + Portugal flags in the "What you're joining" card are inline emoji (🇪🇸🇵🇹) rather than a custom SVG, since the France/Italy single-country flag pattern doesn't apply to a two-country market

---

## Tools & Stack

| Tool | Use |
|---|---|
| HTML / CSS / Vanilla JS | Entire page — no frameworks |
| Halyard Display & Halyard Text | Typography (licensed, embedded as OTF) |
| Loom | Video hosting for the team video (once added) |
| Claude (Anthropic) | All copy, design decisions, and code generation |
| Vercel | Deployment |

---

## Author

Built by Pallavi — Senior Recruiter, Headout (Culture & Talent team).
Designed and developed with Claude (Anthropic) as an AI-assisted recruiting tool.
