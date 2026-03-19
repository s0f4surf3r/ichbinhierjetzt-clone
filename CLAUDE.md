# Doris Website — ichbinhierjetzt-clone

## Überblick
- **Kundin**: Doris R. Mumenthaler — Traumasensibles Coaching, Jin Shin Jyutsu, Dornach (CH)
- **Live**: https://ichbinhierjetzt-clone.statichost.page
- **Repo**: `s0f4surf3r/ichbinhierjetzt-clone` (GitHub)
- **Hosting**: statichost.eu (Helsinki)
- **Stack**: Eleventy 2.0.1 + Nunjucks, Port 9090

## Farbsystem (NICHT 7-Rollen-System!)
Dieses Projekt nutzt semantische Farbnamen statt des globalen 7-Rollen-Systems:
```css
--rosa-dunkel: #C99389   /* Haupt-Hintergrund, Nav, Footer */
--rosa-hell:   #E3AEA6   /* Sekundäre Sektionen */
--weiss:       #FFFFFF   /* Text auf rosa, weisse Sektionen */
--dunkelgrau:  #323335   /* Text auf weiss */
--teal:        #89BFC9   /* Teal-Sektionen, Galerie */
--teal-hell:   #A6DBE3   /* Helle Teal-Variante */
```
Kein Dark Mode. `color-scheme: light only`.

## Fonts
- **Raleway** (light 300) — Headings. Selbst gehostet in `/fonts/`
- **Roboto** (variable) — Body. Selbst gehostet in `/fonts/`
- NICHT Playfair/Source Sans (das ist die alte Doris-Website `Doris_webseite_backup/`)

## Sektions-Klassen
`.section--rosa-dunkel`, `.section--rosa-hell`, `.section--teal`, `.section--teal-hell`, `.section--weiss`, `.section--image`, `.section--bg` (mit `.section-overlay`)

## Blog
- Übersicht: `/texte/` (`src/texte.njk`)
- Einzeltexte: `/texte/:slug/` (Layout: `src/_layouts/text.njk`)
- Collection: `sortedTexte` (tag `text`, kein draft, nach Datum desc)
- DE/EN-Sprachswitch bei Texten mit `translation_en_body`
- Content-Dateien: `src/texte/*.md`

## CMS (perfectCMS)
- Admin-Panel: `/admin/` (`src/admin/index.html`, `app.js`, `style.css`)
- API: `https://perfectcmstm6mdmqs-doris-cms-api.functions.fnc.fr-par.scw.cloud`
- Magic-Link Auto-Login + Inline-Edit Scripts in `base.njk`
- Passthrough: `eleventyConfig.addPassthroughCopy("src/admin")`

## Design-Panel (dev-only)
- Aktivierung: `?panel` URL-Parameter oder `localStorage.setItem('design-panel', true)`
- Slider für: Section Padding, H1/H2/Body Size, Line Height, Content Max-Width
- Manipuliert Element-Styles direkt, nicht CSS Custom Properties
- Nur Dev-Phase — nie in Produktion

## Navigation
Willkommen, Traumasensibles Coaching, Jin Shin Jyutsu, Doris R. Mumenthaler, Kosten, Kontakt, Galerie, Texte

## Build & Deploy
```bash
npx @11ty/eleventy              # Build
npx @11ty/eleventy --serve      # Dev-Server (Port 9090)
```
Deploy: Push zu GitHub → statichost.eu baut automatisch

## Backup / Quelle
`Doris_webseite_backup/` enthält eine ältere Version mit anderem Farbsystem (`--color-fire`, `--color-ember`, `--color-warm` etc.) und anderen Fonts (Playfair Display, Source Sans 3). Admin-Dateien und Texte wurden von dort kopiert und an dieses Projekt angepasst.
