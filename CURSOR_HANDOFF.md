# Now and Then Shopify — Cursor Handoff

## Project goal

Rebuild the supplied Figma file as a Shopify theme with high visual fidelity. The Figma file is the sole visual source of truth. Desktop designs are 1920px wide; homepage fidelity must be verified at 95% or better before final acceptance, followed by responsive layouts and the remaining pages.

Figma: https://www.figma.com/design/01OAZpFO6d43znMmmCoRIy/nowandthen?node-id=1011-1600

Shopify store: `nowandthen-gkymchvf.myshopify.com`

Development preview theme ID: `191457886571`

## Current implementation

### Homepage

- Template: `templates/index.json`
- Section: `sections/nowandthen-home.liquid`
- Styles: `assets/nowandthen-home.css`
- Desktop layout and a first mobile implementation are present.
- Exact Figma-exported images, texture, logo, navigation icons, and footer assets are stored in `assets/nt-*`.
- Announcement close and mobile navigation toggle interactions are implemented.
- This page is **not yet accepted as 95% verified** because a complete 1920px Shopify preview screenshot comparison has not been completed.

Figma nodes:

- Desktop home: `1011:1607` (1920 × 8026)
- Mobile home: `1018:3698` (375 × 6304.95)

### Collection page

- Template: `templates/collection.json`
- Section: `sections/nowandthen-collection.liquid`
- Card snippet: `snippets/nowandthen-collection-card.liquid`
- Styles: `assets/nowandthen-collection.css`
- 1920px desktop structure implemented as a two-column grid with eight exact 640 × 800 Figma container exports.
- Mobile CSS currently exists as a reasonable first pass, but it has not been matched against a dedicated mobile Figma frame.

Figma node: `1011:1752` (1920 × 4590)

### Product detail page

- Template: `templates/product.json`
- Section: `sections/nowandthen-product.liquid`
- Styles: `assets/nowandthen-product.css`
- Two 860 × 1075 exact product images, thumbnail navigation, product information, material selector, add-to-bag state, and three related cards are implemented.
- Shopify product/variant integration is present but requires runtime testing with real products.
- Mobile CSS is only a first pass and has not yet been verified against a mobile Figma frame.

Figma node: `1011:2218` (1920 × 4270)

## Remaining pages

- Interviews: `1011:1945`
- Interview detail: `1011:1886`
- Lookbook: `1011:2114`
- Lookbook detail: `1011:2085`
- Philosophy: `1011:2148`
- Contact: `1049:1492`
- FAQ: `1049:5800`

## Design tokens already established

- Ink: `#2B2823`
- Paper: `#F4F0E8`
- Rust: `#7F4632`
- Taupe: `#9A8D7D`
- Sand: `#D3C4AF`
- Font: Inter
- Body/navigation: 14px, 500, 24px line-height, 0.28px letter-spacing
- Italic links/actions: 14px, 500 italic, 24px line-height, 1px letter-spacing
- Paper texture: `assets/nt-texture.png`

## Validation status

- `shopify theme check` passes with 11 warnings, all inherited from the original Dawn/Horizon theme files.
- `git diff --check` passes.
- The Shopify development watcher is running from Codex and syncing changes to preview theme `191457886571`.
- Storefront visual validation is currently blocked by the Shopify storefront password screen. The previously supplied `newclu` value is not the storefront password.
- Do not claim 95% fidelity until an actual 1920px browser screenshot has been compared with Figma.

## Collaboration rules

1. Do not edit these files while Codex is editing the same page:
   - `sections/nowandthen-home.liquid`
   - `assets/nowandthen-home.css`
   - `sections/nowandthen-collection.liquid`
   - `assets/nowandthen-collection.css`
   - `sections/nowandthen-product.liquid`
   - `assets/nowandthen-product.css`
   - `templates/index.json`
   - `templates/collection.json`
   - `templates/product.json`
2. Cursor should take one of the remaining pages and create new, page-specific files instead of rewriting the three pages above.
3. Prefix new custom assets and CSS with `nt-` or `nowandthen-`.
4. Download Figma image assets into the repository; do not leave expiring Figma URLs in Liquid or CSS.
5. Do not start a second `shopify theme dev` process while the existing watcher is running.
6. Run `shopify theme check` and `git diff --check` after changes.
7. The repository currently has no initial commit. Create a safe baseline commit before simultaneous editing or use separate branches/worktrees.

## Recommended Cursor assignment

Implement the Contact page (`1049:1492`) in new files only:

- `sections/nowandthen-contact.liquid`
- `assets/nowandthen-contact.css`
- `templates/page.contact.json`
- any new exact Figma exports under `assets/nt-contact-*`

Do not modify homepage, collection, product-detail, or their templates. Match the 1920px Figma frame first, add responsive behavior without changing desktop geometry, and return a list of modified files plus validation results.
