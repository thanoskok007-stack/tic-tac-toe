# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the game

Open `index.html` directly in a browser — no build step or server required:

```
open index.html
```

## Architecture

The entire project is a single file: `index.html`. It contains three sections in order:

1. **CSS** (`<style>`) — dark-themed UI. Color palette: `#e94560` (red, player X / accent), `#4cc9f0` (blue, player O), `#1a1a2e` (page background), `#16213e` (card/cell background), `#0f3460` (hover/highlight).

2. **HTML** — static markup for the score panel, status line, 3×3 board (nine `.cell` divs with `data-index` 0–8), and a "New Game" button.

3. **JavaScript** (`<script>`) — all game logic, no frameworks or dependencies:
   - `WINS` — the 8 winning index triplets, checked after every move.
   - `board` (array[9]), `current` ('X'|'O'), `gameOver`, `scores` — all mutable game state, reset by the "New Game" button.
   - Click handler on each cell: updates state, adds CSS classes (`taken`, `x`/`o`, `winner`), and calls `checkWin()` / `updateScores()`.
   - `checkWin()` returns the winning triplet or `null`.
   - `updateScores()` writes score values into the DOM by ID.

## Git workflow

Every meaningful change should be committed and pushed to GitHub:

```
git add index.html
git commit -m "descriptive message"
git push
```

Remote: `https://github.com/thanoskok007-stack/tic-tac-toe`
