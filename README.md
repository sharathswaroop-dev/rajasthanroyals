# RR Pressure Selector

Who delivers when the match is on the line? An interactive auction-room dashboard for the Rajasthan Royals that rates IPL and T20I batters and bowlers on how they perform in high-pressure moments, using ball-by-ball data from 2022 onwards.

Built for **SupeRR Selector Season 2, Round 1**.

## What is in the dashboard
1. **Current squad**: every squad player placed against all ranked players (Top 10, upper, middle or lower third, or low sample).
2. **Problem statement**: how pressure is defined, how every ball is scored, and how the rating is built, step by step.
3. **Auction look-out**: ranked players outside the squad, with an "Upgrade" flag against the squad's best Indian player in the same role.
4. **Auction plan**: purse, shortlist and role gaps.
5. **Finishers** and 6. **Bowlers**: sortable, filterable tables with a shortlist you can copy.

A switch at the top chooses the ratings: **IPL + T20I**, **IPL only** or **T20I only**.

## The method in four lines
- A win-probability model scores the match at every ball; the top 20% of balls by how far one ball can swing the win chance are **pressure balls**.
- Every ball earns win-probability points (a dot at the death of a chase costs about 2.5 times a powerplay dot).
- Players are compared with an average player against the same opponents, on the same ground, in the same role, with small samples pulled toward average.
- The final score combines the pressure rating with consistency, run-rate arc (batters), a 0-10 impact mark and match-shaping innings or spells.

The full explanation is the *Problem statement* tab in the app.

## Files
| File | What it is |
|---|---|
| `index.html` | The dashboard (single self-contained file, data embedded). Served at the site root. |
| `RR_Pressure_Selector.html` | Same dashboard under its submission file name. |
| `all_players_table_{both,ipl,t20i}.csv` | Every player's ratings for each view. |
| `dev.js` | Tiny local server: `npm run dev`, then open http://localhost:5173. |
| `vercel.json` | Static hosting config (security headers, CSV caching). |

## Run locally
```bash
npm run dev     # or: node dev.js
```
Or just open `index.html` in a browser; there is no build step.

## Limits to keep in mind
Even the busiest players have only 120 to 600 pressure balls, so intervals are wide. Auction pool, contracts and prices are not in the data, and nationality is inferred for players with only franchise appearances. These are best estimates from about 3.5 seasons of data, not guarantees.
