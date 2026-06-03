# IIIF as an Ethical Access Layer for AI

A static HTML slide deck for the “IIIF as an Ethical Access Layer for AI” Birds of a Feather session at the IIIF Annual Conference 2026 in Leiden, Netherlands.

The deck frames IIIF as infrastructure for responsible machine reuse of cultural heritage materials, with emphasis on metadata context, provenance, consent, crawler behavior, and community-led design principles.

## Project Structure

```text
.
├── index.html          # Slide deck markup
├── styles/main.css     # Slide layout and visual styling
├── images/             # Source images and generated WebP assets
├── resize_images.sh    # Resize oversized PNG/JPEG images
└── generate_webp.sh    # Generate WebP versions of PNG/JPEG images
```

## Viewing the Deck

Open `index.html` directly in a browser:

```sh
open index.html
```

You can also serve it locally if you prefer browser-style local URLs:

```sh
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Editing Slides

Slides are defined as `.slide-container` sections in `index.html`. Each slide has a stable ID such as `slide1`, `slide2`, and so on.

Shared colors, typography, layout primitives, and slide-specific styles live in `styles/main.css`.

The deck currently uses externally hosted Google Fonts and Font Awesome icons, so an internet connection is needed for the intended typography and icons unless those assets are vendored locally.

## Image Workflow

Images live in `images/`. The HTML references WebP assets where available.

Resize large source images before generating WebP files:

```sh
./resize_images.sh
```

Generate WebP files:

```sh
./generate_webp.sh
```

Regenerate all WebP files, including ones that already exist:

```sh
./generate_webp.sh --all
```

## Requirements

The slide deck itself only requires a modern browser.

The image helper scripts require:

- ImageMagick for `resize_images.sh`
- `cwebp` from the WebP tools package for `generate_webp.sh`

On macOS with Homebrew:

```sh
brew install imagemagick webp
```

## Notes

This project is intentionally lightweight: there is no build step, package manager, or JavaScript runtime required for the deck.
