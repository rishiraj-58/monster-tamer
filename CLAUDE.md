# Monster Tamer: Architecture & Workflow Guidelines

## Project Context
Monster Tamer is a 2D RPG built with Vanilla JavaScript and the Phaser 3 framework. It uses a strict Scene-based architecture, grid-based movement in the overworld, and a State Machine for the turn-based battle system.

## Code Style & Architecture
- **Vanilla JS & JSDoc:** We do not use TypeScript. You must use JSDoc comments rigorously to define object shapes, parameters, and return types for all new classes and methods.
- **Phaser Native:** Do not reinvent the wheel. Rely on native Phaser 3 utilities (e.g., `Phaser.Math`, `Phaser.Time.TimerEvent`, `Phaser.Events.EventEmitter`) instead of writing custom math or event buses.
- **Data-Driven Design:** Do not hardcode monster stats, attacks, or level data in the JavaScript classes. Always ingest this from the `assets/data/` JSON files using the `DataManager`.
- **State Management:** Complex flows (like battles or cutscenes) MUST use the existing `StateMachine` utility (`src/utils/state-machine.js`).

## Git & Workflow (CRITICAL)
- **Dependencies:** DO NOT install any npm packages. The game runs natively in the browser via an HTTP server.
- **Destructive Actions:** Never execute destructive git commands without explicit user confirmation.
- **Memory Leaks:** When modifying `Scenes`, you must ensure that any custom event listeners or timers are properly destroyed in the Scene's `shutdown` or `destroy` methods.