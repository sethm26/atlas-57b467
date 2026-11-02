# Where To Points: demo

A static demo of an award flight search engine and map. Pick a departure airport, and the page
shows what a trip would cost in points across more than 20 airline programs, priced for each credit card's
transfer ratio, on a self-hosted vector globe.

**Every fare in this demo is generated.** Prices come from distance, cabin and program rules, so
nothing here is real availability. The real project's data never leaves its own server.

## What this demo shows

- **Search:** one-way and round trips, cabin, card, and filters, with a cheapest-by-day calendar
  and the best way to book each fare.
- **Routes and Deals:** every route with fares, plus a regional cheat sheet of the cheapest
  destinations and best-value programs.
- **A map that needs no key:** MapLibre GL with a single PMTiles file, so the page makes no
  outside requests.
- **Runs without a server:** the live site answers searches from an API over a SQLite database.
  This copy uses the same page with a saved per-airport snapshot, so searches run in the browser.

## How the real project works

- A scheduler spreads a daily call budget over every route a fare source tracks, busiest
  airports first, and resumes across days.
- A small read-only search API (Python standard library, SQLite, indexed lookups, per-query time cap)
  serves Search, Routes and Deals.
- Prices are normalized into card points using verified, dated transfer-ratio tables.
- Fares are colored by value against a typical price for comparable routes.

Built by Seth Mullins.
