# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a vanilla web project — no build system, no dependencies, no package manager. All code runs directly in the browser by opening HTML files.

## Running the Project

Open any HTML file directly in a browser:

```bash
open tictactoe.html
```

There is no build step, server, or compilation required.

## Git & GitHub Workflow

All changes must be committed and pushed to GitHub at https://github.com/ribciuc/claude-test-1.

- Commit after every meaningful change
- Push immediately after committing
- Use descriptive commit messages that explain *why*, not just *what*
- Always include the co-author trailer:
  ```
  Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>
  ```

## Code Architecture

Each game/feature is a **single self-contained HTML file** with inline CSS (`<style>`) and inline JavaScript (`<script>`). There are no external dependencies, modules, or shared files.

### tictactoe.html structure

- **State**: `cells` (flat 9-element array), `current` (active player), `gameOver`, `scores`
- **Board rendering**: cells are created dynamically by `init()` and appended to `#board` (CSS grid)
- **Win detection**: `checkWin()` tests `cells` against the `WINS` constant (8 hardcoded winning index triples)
- **DOM sync**: cell state is tracked in both the `cells` array and via CSS classes (`.x`, `.o`, `.taken`, `.win`)

## Design Conventions

- Dark theme: background `#1a1a2e`, accent red `#e94560`, accent blue `#a8dadc`
- No frameworks — plain DOM APIs only
- Scores persist across rounds within a session (reset on page reload)
