# German-Czech Flashcards

Static German-Czech flashcards with local MP3 pronunciation and a simple browser-based spaced repetition system.

## Requirements

- macOS
- `ffmpeg` installed
- macOS German voice `Yannick (Enhanced)` installed and working

You can test the voice with:

```bash
say -v "Yannick (Enhanced)" "das Haus"
```

## Generate audio and cards

Run:

```bash
python3 generate.py
```

This reads `vocab.json`, creates MP3 files in `audio/`, and writes `cards.json`.

## Run locally

Run:

```bash
python3 -m http.server 8000
```

Open:

```text
http://localhost:8000
```

## Process all vocabulary

The MVP only processes the first 10 entries:

```python
LIMIT = 10
```

To process the full vocabulary list, change it to:

```python
LIMIT = None
```

Then run:

```bash
python3 generate.py
```

## Deployment

Because this is a static site, it can later be deployed to GitHub Pages, Netlify, or another static hosting service. Deploy these files:

```text
index.html
cards.json
audio/
```

Keep in mind that the `audio/` folder can become large when generating all words. Do not commit or deploy large audio files unless you are sure they are needed.

## Troubleshooting

### Voice not found

Check installed voices in macOS System Settings or run:

```bash
say -v "Yannick (Enhanced)" "das Haus"
```

If the voice is missing, install it first or update `VOICE` in `generate.py`.

### ffmpeg not found

Install `ffmpeg`, then verify:

```bash
ffmpeg -version
```

### cards.json fails to load

Use a local server instead of opening `index.html` directly:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

### Audio does not play

Run `python3 generate.py` and confirm the referenced MP3 files exist in `audio/`. Browser audio playback also requires a user action, so use the down arrow control or `ArrowDown`.
