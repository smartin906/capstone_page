## Repository overview

- This repo is a minimal single-page capstone site. The primary source is `martin_capstone_page.html` at the repository root.
- The HTML is fully self-contained: styles are inline in the document head (CSS custom properties + responsive rules), and a small script at the bottom only updates the footer year.
- Images and video in the page are placeholders (external `picsum.photos` URLs and `your-video.mp4` in markup). There is no `assets/` directory by default.

## What an AI agent should know first (big picture)

- There is no build, bundler, or test framework. This is a static HTML preview project — editing the single file and opening it in a browser is the normal workflow.
 - The document uses semantic sections with stable IDs (for example: the ids hook, problem, research, process, media). The header navigation links map directly to these section ids.
 - Visual/theme behavior (including dark mode) lives in the <head> style block and uses the prefers-color-scheme media query. Keep theme edits inside the inline styles unless you intentionally split CSS out.

## Common tasks and explicit examples

- To preview locally: serve the folder and open `martin_capstone_page.html` in a browser. Simple example (macOS/zsh):

```bash
# from the repository directory
python3 -m http.server 8000
# then open http://localhost:8000/martin_capstone_page.html
```

- To add a new section visible in the nav: add a new navigation list item that links to the section id and add a corresponding section element with that id and a heading later in the document. For example, choose the id my-section and add a nav entry that links to it, then add a section with id my-section and an H2 heading.

- To add local assets: place images/videos next to the HTML (e.g., `assets/`), reference them with relative paths (`assets/my-image.jpg`) and update the `<img>`/`<video>` src attributes.

## Conventions & patterns discovered in the codebase

- Accessibility: the page includes a skip link (`.skip`), uses semantic `<main>`, `<section>`, `<nav aria-label>` and keyboard-focus styles. Preserve or improve these when editing.
- Layout: grid classes like `.grid` and `.grid-2` are used for responsive card layouts — add those classes to maintain consistent spacing.
- Cards and callouts use `.card` and `.callout` with consistent border/background variables; prefer reusing these classes for new content blocks.

## When editing content, prefer these rules

1. Preserve section IDs. Other code (nav) relies on them.
2. Keep global design tokens in the :root CSS block (colors, radius, max width) if you modify theme values.
3. Use external placeholder images only for mockups — replace with relative/local assets before final delivery.

## Debugging & developer workflow

- No build step — troubleshooting is primarily visual. Use the browser DevTools to inspect layout and color variables.
- If you split CSS/JS out into separate files, update the repo README (or add one) describing the new workflow and how to serve the site locally.

## Integration points & external dependencies

- External fonts: Google Fonts are referenced from the head (`Source Serif 4`). If offline use is required, download and serve fonts locally and update the link.
- Placeholders: `picsum.photos` and `your-video.mp4` are used. Replacing these requires adding local assets and editing the `src` attributes.

## Commit & PR suggestions for AI agents

 - Make small, atomic commits. Examples of good commit messages for this project:
   - content: add research findings to research section
   - fix: update hero copy and tags
   - chore: add local assets and update image paths

## What not to change without confirmation

- Significant structural changes (splitting into multiple pages, introducing a bundler) — ask the repo owner first.
- The semantic section IDs and nav ordering — these are relied on for internal navigation.

## Files to inspect for context

- `martin_capstone_page.html` — single source of truth for layout, content, and styles.

---
If anything in the instructions above is unclear or you'd like me to include example edits (for instance, extracting CSS into `styles.css` or creating an `assets/` folder and relocating images), tell me which change you'd prefer and I will update the repo and these instructions accordingly.
