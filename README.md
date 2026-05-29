# Hairline

**A one-file CSS reset for editorial layouts.**

Hairline is a surgical reset for type-first, reading-first interfaces. It isn't a framework, a component library, or an opinionated design system. It's a single `.css` file that gives your editorial HTML honest, beautiful defaults — and gets out of the way.

→ **[Live demo](https://nsimona.github.io/hairline)**  
→ **[simonanasteva.com](https://simonanasteva.com)**

---

## What's inside

| Section | What it does |
|---|---|
| **Design tokens** | Full set of CSS custom properties — type scale, spacing, measure, leading, tracking, ink/surface colors, radius, motion |
| **Box model** | Universal `border-box`, zeroed margins, `min-width: 0` to prevent grid/flex inflation |
| **Document & body** | Serif body font stack, font smoothing, text rendering, `prefers-reduced-motion` |
| **Type scale** | Minor-third (×1.200) scale from `--text-xs` to `--text-5xl` |
| **Headings** | Weight-400 with tight leading, negative tracking, `text-wrap: balance` |
| **Body copy** | `text-wrap: pretty`, dropcap, kicker/eyebrow, lede, pullquote, smallcaps |
| **Lists** | Disc, decimal, nested, bare reset via `[role="list"]`, definition lists |
| **Links** | Accent color, offset underlines, `skip-ink`, external `↗` via `[target="_blank"]` |
| **Media** | Block display, aspect-ratio preservation, `figure` + `figcaption` |
| **Tables** | Collapsed borders, zebra striping, tabular-nums, `[data-type="number"]` alignment |
| **Forms** | Normalised inputs, custom select arrow, smooth focus rings, accessible buttons |
| **Code** | Inline `code`, `pre` blocks, `kbd` lift — all in JetBrains Mono |
| **Horizontal rules** | Plain, ornament (`[data-ornament]`), labelled (`[data-label]`) |
| **Utilities** | `.sr-only`, `.measure`, `.lede`, `.pullquote`, `.capo`, `.smallcaps`, `.muted`, `.faint` |
| **Print** | Clean black output, expanded link URLs, orphan/widow control |

---

## Installation

**Download directly:**
```
curl -O https://raw.githubusercontent.com/simonanasteva/hairline/main/hairline.css
```

**Or copy-paste** the single file into your project — it has no dependencies.

**Link from HTML:**
```html
<link rel="stylesheet" href="hairline.css">
```

That's it.

---

## Usage

### Tokens

Everything is a CSS custom property. Override them in your own `:root` block after importing hairline:

```css
@import "hairline.css";

:root {
  --color-accent: hsl(340 80% 50%);  /* your brand color */
  --measure: 70ch;                    /* your preferred line length */
}
```

### Dark mode

Dark mode is automatic via `@media (prefers-color-scheme: dark)`. To force light or dark:

```html
<html data-theme="dark">
```

```css
[data-theme="dark"] { color-scheme: dark; }
```

### Dropcap

```html
<p data-dropcap>The first letter becomes large and floated…</p>
```

### Eyebrow / kicker label

```html
<span data-kicker>Culture</span>
<h2>The weight of small decisions</h2>
```

### External link indicator

The `↗` is added automatically via CSS to any `<a target="_blank">`. Suppress it:

```html
<a href="…" target="_blank" data-no-external>GitHub</a>
```

### Ornament divider

```html
<hr data-ornament>
```

### Bare list (no bullets, no padding)

```html
<ul role="list">…</ul>
```

### Numeric table column

```html
<td data-type="number">1,200,000</td>
```

### Utilities

```html
<p class="lede">A larger, muted intro paragraph.</p>
<p class="measure">Constrained to 65ch for reading comfort.</p>
<blockquote class="pullquote">A floated editorial quote.</blockquote>
<span class="smallcaps">The New York Times</span>
```

---

## Design decisions

**Why serif?**  
Hairline is opinionated about one thing: editorial type belongs in serif. The body font stack (Iowan Old Style → Palatino → Georgia) is chosen to read beautifully at long-form length. If you're building a product UI, layer your own `font-family` on top.

**Why weight 400 headings?**  
Bold headings fight the text. Light headings create hierarchy through size alone — a more considered, magazine-like hierarchy.

**Why `min-width: 0`?**  
Without it, flex and grid children can overflow their containers when content is wide. This is the silent cause of a hundred layout bugs.

**Why `text-wrap: pretty`?**  
Prevents single-word orphans on the last line of a paragraph — a subtle but meaningful typographic improvement in modern browsers.

**Why `65ch` measure?**  
Research consistently puts comfortable reading width between 45–75 characters. `65ch` is the sweet spot for body copy. Adjust via `--measure`.

---

## Browser support

All modern browsers. IE is not supported and will not be.

| Feature | Support |
|---|---|
| CSS custom properties | Chrome 49+, Firefox 31+, Safari 9.1+ |
| `text-wrap: balance` | Chrome 114+, Firefox 121+, Safari 17.4+ |
| `text-wrap: pretty` | Chrome 117+, Firefox 127+ |
| `accent-color` | Chrome 93+, Firefox 92+, Safari 15.4+ |

For `text-wrap` in older browsers, the line simply wraps normally — no breakage, just no enhancement.

---

## File size

```
hairline.css   ~10 KB unminified
               ~5 KB gzipped
```

---

## Contributing

Issues and PRs welcome. The scope is intentionally narrow — this is a reset, not a framework. Contributions that add tokens, fix browser inconsistencies, or improve accessibility are most welcome. Contributions that add components will be declined.

---

## License

MIT — [simonanasteva.com](https://simonanasteva.com)
