# Regrowing the heart

A deep-zoom map of 12,185 research papers on heart regeneration (OpenAlex, CC0), one dot per paper, placed by the
words in its title and abstract — as a static page.

Live: https://youdata.github.io/heart-regen/

Find any paper by its title or DOI, or click a dot, for its card (topic, journal, year, citations, a link to the
paper); close in, the papers' titles are drawn, the most cited first. Colour the map by topic or by year; the title,
the keys, the papers-a-year chart (transplanted cells vs the heart's own cells) and the sources are in a panel beside
it. A five-stop tour (▶ Play) walks through it.

The two image pyramids (`heart-topic/`, `heart-year/`: `header.idx` + `{z}/{x}/{y}.png`) are tile folders, so any
static host serves them; the fonts are in `fonts/`, trimmed to the page's characters. The narrated video is not included.

## How it is made

From `rx-infographic-skill/examples/heart-regen` (its README has the pipeline: OpenAlex → TF-IDF/LSA → UMAP → topics →
tiles → `build.mjs`), with rx (`~/rx-cli`):

```sh
node build.mjs                                       # → heart-regen.json
rx export heart-regen.json --out site --app /rx-graphic-editor/web/index.html \
   --canvas --theme dark --lock-layers --hide P,V2,T2 --tiles dir
rx publish site --to github:youdata/heart-regen --yes
```
