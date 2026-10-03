# VOID DRIFT

A fast, minimalist arcade survival game that runs in the browser. You pilot a small ship through a field of drifting debris, collect shards to boost your score multiplier, and try to last as long as you can. It is a single HTML file with no build step and no dependencies.

Made by Vikrant.

## How to play

- **Dodge the coral debris.** One hit ends the run.
- **Collect the amber shards** that fall from the top of the screen. Each shard gives bonus points and pushes your multiplier up faster.
- **Survive.** Your score climbs the longer you stay alive, and the multiplier grows over time.
- **Watch your trail.** It changes color as your multiplier rises:

| Multiplier | Trail color |
| --- | --- |
| Below x2.0 | Cyan |
| x2.0 and above | Violet |
| x3.5 and above | Gold |

The multiplier goes up in steps of 0.5 and tops out at **x5.0**.

## Controls

| Input | Action |
| --- | --- |
| Mouse | The ship drifts toward your cursor |
| Arrow keys or WASD | Thrust in that direction |

When you press a movement key, the keyboard takes priority over the mouse until you let go.

## Difficulty

The game gets harder the longer you survive. Debris falls faster and spawns more often as the run goes on, until it reaches a fixed maximum spawn rate. Rocks enter from the top and from the sides.

## Getting started

1. Download `void-drift.html`.
2. Open it in any modern desktop browser (Chrome, Edge, Firefox, Safari).
3. Click **Launch**.

You can also host the file on any static host, such as GitHub Pages or Netlify.

## Scoring

- Score increases continuously while you survive, scaled by your current multiplier.
- Each amber shard adds **25 points** and speeds up your next multiplier step.
- Your best score is shown on the game-over screen. It is kept only while the page stays open and resets when you reload.

## Tech

HTML5 Canvas, CSS and vanilla JavaScript, with no libraries. The game loop uses `requestAnimationFrame` with a capped time step, so it behaves the same on screens with different refresh rates. The canvas resizes to fill the window.

The interface font is JetBrains Mono if it is installed on your computer. Otherwise it falls back to Consolas or the system monospace font.

## Known limitations

- **Desktop only for now.** The game reads mouse and keyboard input, and has no touch controls.
- **Best score is not saved** between sessions.
- There is no sound.

## Customizing

Everything is in the one file. A few values you might want to change in the `<script>` section:

- **Ship handling**: `targetSpeed`, the thrust value `0.9`, and the friction value `0.86`.
- **Difficulty**: the rock `speed` formula in `spawnRock()` and the `spawnRate` calculation in `update()`.
- **Multiplier cap and steps**: `Math.min(5, state.mult + 0.5)`.
- **Shard bonus**: `state.score += 25`.
- **Colors**: the `trailColor()` function and the CSS at the top of the file.
