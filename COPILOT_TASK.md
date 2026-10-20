# Task: reusable scripts for AleNeural A51 concept previews

Owner: sitihasnah109-create. Repository: AleNeural-AI-System-OS (private).

## Goal

Create reusable build and validation scripts so later visual revisions require small configuration/CSS edits and short review summaries. Work in one branch and open one draft pull request for Baba/Codex review. Do not merge or publish automatically.

## Source of truth

Extract the tracked `AleNeural-Preview-v7-Source.zip` into the repository root, preserving its paths. It contains `src/preview.template.html`, four original PNG assets, a dependency-free baseline builder, package.json and README. Run `npm run build` before editing. The resulting `dist/index.html` must match the baseline SHA-256 recorded in `BASELINE.json` inside the archive. The ZIP and baseline record are immutable references.

The visual baseline is v7, derived from the second supplied v5 reference. Preserve its neon cyan/purple style, four reference images and current interactions. Do not generate replacement artwork or redesign the screen during this refactor.

## Implementation requested

1. Keep images in separate assets, never paste base64 image data into editable source, instructions, logs or review messages. Embed images only in the standalone build output.
2. Introduce documented, small layout/theme configuration for clock visibility/position, weather/location position, battery percentage position, Sonordroid–AleCore label position, and the simple Hey AleCore control position/style. Default values must reproduce v7.
3. Provide portable Node.js scripts for deterministic build, local preview, validation and optionally watch mode. Use minimal dependencies. No global tools, credentials, paid services or AI API calls are needed. Bind the local preview server to loopback only.
4. Build a self-contained HTML file and a compact JSON report (revision, artifact path, bytes, SHA-256, image hashes, validation result). Put generated outputs in ignored `dist/`. Preserve immutable previous revision artifacts when explicitly archiving a new revision; fail on conflicting archive names.
5. Add meaningful checks: configuration validation, exactly four unchanged image hashes, no unresolved placeholders, reproducible build, smoke tests for all tabs, listening/stop/Escape, portal/apps/back and keyboard navigation. Add browser layout checks that verify the single Home clock, battery percentage placement and absence of unintended overlap at representative viewport sizes. Inspect the existing UI before choosing selectors.
6. Add GitHub Actions to run the build and validation on pull requests, upload the standalone preview/report as artifacts, and produce a concise result summary. Deterministic automation only; no automatic AI/rewrite loop. Pin tool versions and document setup. If browser tooling is needed, install it through its official package manager.
7. Document normal edit/build/check/archive commands and a short revision checklist in Indonesian. Keep reviews concise: changed files, commands and results, preview artifact, remaining limitations. Do not include giant HTML diffs or image blobs in issue comments.

## Acceptance

- The initial baseline build matches BASELINE.json. The refactor retains the same four assets and visible v7 layout/flows; explain any unavoidable byte differences after the refactor and verify visual behavior.
- Home: no small status-bar clock; one main clock near the top; raised weather/location; `100%` inside the battery; lowered Sonordroid–AleCore text; lowered simple Hey AleCore text/mic.
- All tabs, simulation and keyboard flows remain usable. No clipping at tested viewport sizes, with screenshots attached to the PR when supported.
- Build/test scripts run on Windows and Linux with documented Node.js versions; CI checks pass or exact blockers are reported.
- One draft PR only. Do not claim tests passed without running them. Summarize any blocked test with its exact safe error.

## Boundaries

This task is HTML concept-preview work only. Do not use ADB, connect to a phone, install APKs, change Android settings/root/launcher/firmware, or call real microphone/location/device APIs. No external telemetry, network integrations, deployment or public sharing. Do not request credentials or change account permissions/billing. Do not import any other local workspace files. Baba provides later concepts gradually; this task establishes the reusable tooling for those revisions.
