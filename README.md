# Is it worth it?

A tiny static webpage that converts an impulse purchase into its retirement-day opportunity cost. Single `index.html`, no build, mobile-first, installable to your home screen.

## Features

- 4 one-click presets (Coffee · Take-Out · Lunch · Night Out) + Custom
- Tap the dollar amount to edit it inline — switches to Custom automatically
- Tap the years number for a session-only override
- Toggle between **Today's $ (7% real return)** and **Future $ (10% nominal return)**
- Settings (gear icon) stores birth year + retirement age in `localStorage` so years-remaining auto-decrements
- iOS/Android "Add to Home Screen" runs it in standalone mode with an app icon

## Run locally

Just open `index.html` in a browser. For full PWA features (manifest, install prompt), serve over HTTP:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy to GitHub Pages

1. Create a new repo on GitHub (e.g. `is-it-worth-it`) and push:
   ```sh
   git remote add origin git@github.com:<you>/is-it-worth-it.git
   git push -u origin main
   ```
2. Repo → **Settings → Pages** → Source: `Deploy from a branch`, Branch: `main` / root.
3. Wait ~1 min, then visit `https://<you>.github.io/is-it-worth-it/`.
4. On your phone, open in Safari/Chrome → Share → **Add to Home Screen**.

## Math

- Real toggle: `FV = PV × 1.07^years` — S&P 500 long-run real return ≈ 7%, so the future number is in today's purchasing power.
- Nominal toggle: `FV = PV × 1.10^years` — headline historical S&P 500 return, in future dollars.

## Backlog (next session)

- **Recurring / subscription mode** — annuity future-value math (e.g. `$15/mo` invested through retirement), with a monthly/weekly toggle on Custom. Dropped from MVP to keep the UI single-purpose.
