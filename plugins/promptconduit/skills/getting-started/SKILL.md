---
name: getting-started
description: Walk a user through installing the PromptConduit CLI and wiring it into their AI coding assistant (Claude Code, Cursor, or Gemini CLI). Use when the user asks how to set up PromptConduit, install hooks, capture events, or get started.
---

# PromptConduit: Getting Started

PromptConduit captures raw events from AI coding assistants (Claude Code, Cursor, Gemini CLI) and forwards them to the PromptConduit platform for observability, analytics, and replay.

## Install the CLI

Homebrew (macOS / Linux):

```bash
brew tap promptconduit/tap
brew install promptconduit
```

Or download a binary directly from [github.com/promptconduit/cli/releases](https://github.com/promptconduit/cli/releases).

## Authenticate

Sign in at [promptconduit.dev](https://promptconduit.dev) and grab an API key. Then:

```bash
promptconduit config env use prod
promptconduit config set-api-key <your-key>
promptconduit test
```

`promptconduit test` confirms the CLI can reach the platform and the key is valid.

## Install hooks for your AI assistant

Pick the tools you use:

```bash
promptconduit install claude-code
promptconduit install cursor
promptconduit install gemini-cli
```

Each command writes the appropriate hook config for that tool. After running it, every prompt/response/tool-call from that assistant will be forwarded to the platform.

## Verify

```bash
promptconduit status
```

Should report each installed integration as healthy. Trigger a quick interaction with the AI assistant, then check your dashboard at [promptconduit.dev](https://promptconduit.dev) to confirm events arrived.

## Backfill history

Already have transcripts on disk from before you installed?

```bash
promptconduit sync
```

This parses local transcript files and uploads them.

## Troubleshooting

- **Events not appearing:** run `promptconduit test`. If it fails, check `promptconduit config show` for the wrong environment or stale key.
- **URL mismatch errors:** unset `PROMPTCONDUIT_API_KEY` in your shell — the CLI uses the config file at `~/.config/promptconduit/config.json` and a shell var will override the env.
- **Uninstall a hook:** `promptconduit uninstall <tool>` removes it cleanly.

## Links

- CLI: [github.com/promptconduit/cli](https://github.com/promptconduit/cli)
- Platform: [promptconduit.dev](https://promptconduit.dev)
- Issues: [github.com/promptconduit/cli/issues](https://github.com/promptconduit/cli/issues)
