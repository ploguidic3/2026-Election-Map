# 2026 Senate flip benchmarks

A static dashboard that shows the swing from the 2024 presidential vote needed
to flip each 2026 Senate seat, and the benchmark margin that swing implies in
every county. Enter county results as they finish to compare them with the
benchmark.

Open `index.html` in a browser. It needs no server or build step.

## How it works

- Margins are two-party: (Dem − Rep) / (Dem + Rep). Third-party votes are ignored.
- The statewide swing needed is the target margin minus the 2024 presidential
  margin. The target defaults to a tie and the winner defaults to the party not
  holding the seat.
- County benchmarks hold 2024 turnout fixed and are solved so that they add up
  to the target statewide margin.
  - **Uniform**: every county moves by the same number of points (capped at ±100).
  - **Proportional**: every county moves by the same amount on the log-odds
    scale, so lopsided counties move less.
- For counties marked complete, "Vs benchmark" is the 2026 margin minus the
  benchmark. The summary averages it weighted by 2026 two-party votes and adds it
  to the target to give a projected statewide margin.
- Entries are saved in the browser's local storage, per state.

For Nebraska, enter the independent challenger's votes in the Dem column.

## Data

- `data/pres2024.js`: 2024 presidential results by county (Alaska by state house
  district) from
  [tonmcg/US_County_Level_Election_Results_08-24](https://github.com/tonmcg/US_County_Level_Election_Results_08-24).
  Rebuild with `python scripts/build_data.py`.
- `data/senate2026.js`: the 35 races and the party holding each seat. Edit it if
  a seat changes hands before the election.
