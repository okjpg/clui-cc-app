# Clui CC App — macOS Desktop App for Claude Code

A customized, standalone macOS desktop app for [Claude Code](https://docs.anthropic.com/en/docs/claude-code), built as an Electron `.app` you can run from Spotlight — no terminal needed.

**Based on [Clui CC](https://github.com/lcoutodemos/clui-cc) by [@lcoutodemos](https://github.com/lcoutodemos).** All credit for the original project goes to the author. This is a customized fork with additional features for macOS power users.

## Demo

[![Watch the demo](https://img.youtube.com/vi/NqRBIpaA4Fk/maxresdefault.jpg)](https://www.youtube.com/watch?v=NqRBIpaA4Fk)

<p align="center"><a href="https://www.youtube.com/watch?v=NqRBIpaA4Fk">▶ Watch the original demo on YouTube</a></p>

## What's different from the original?

This fork adds features focused on productivity and native macOS experience:

### Standalone macOS App
- Build a native `Clui CC.app` with `npm run dist` — no terminal required
- Open from Spotlight, Launchpad, or Applications folder like any Mac app

### Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Cmd+T` | New tab |
| `Cmd+W` | Close current tab (not the app) |
| `Cmd+1..9` | Switch between tabs |

### Pinned Tabs
- **Right-click** a tab to pin/unpin
- Pinned tabs stay on the left, can't be closed accidentally
- Persist across app restarts — reopen the app and your pinned projects are back with full conversation history

### Tab Rename
- **Double-click** a tab title to rename it inline
- Enter to confirm, Escape to cancel

### macOS Spaces Fix
- Window follows the active Space/desktop when toggled — no more jumping to the wrong desktop

## All Original Features

- **Floating overlay** — transparent, click-through window that stays on top (`Alt+Space`)
- **Multi-tab sessions** — each tab spawns its own `claude -p` process
- **Permission approval UI** — review and approve/deny tool calls from the UI
- **Conversation history** — browse and resume past sessions
- **Skills marketplace** — install plugins from Anthropic's GitHub repos
- **Voice input** — local speech-to-text via Whisper
- **File & screenshot attachments** — paste images or attach files directly
- **Dual theme** — dark/light mode with system-follow option

## Install

### Prerequisites

- **macOS 13+**
- **Node.js 18+** (`brew install node`)
- **Claude Code CLI** (`npm install -g @anthropic-ai/claude-code`)
- **Xcode Command Line Tools** (`xcode-select --install`)
- **Python setuptools** (`python3 -m pip install --upgrade pip setuptools`)

### Build the app

```bash
git clone https://github.com/okjpg/clui-cc-app.git
cd clui-cc-app
npm install
npm run dist
```

### Install to Applications

```bash
cp -R "dist/mac-arm64/Clui CC.app" /Applications/
```

Then open from **Spotlight** (`Cmd+Space` → "Clui CC") or the Applications folder.

> **Note:** The app is not code-signed. On first launch, macOS may block it — go to **System Settings → Privacy & Security** and click **Open Anyway**.

### Quick start (without building the app)

If you prefer running from terminal:

```bash
./commands/setup.command
./commands/start.command
```

## Development

```bash
npm install
npm run dev
```

Renderer changes update instantly. Main-process changes require restarting `npm run dev`.

| Command | Purpose |
|---------|---------|
| `./commands/setup.command` | Environment check + install dependencies |
| `./commands/start.command` | Build and launch from source |
| `./commands/stop.command` | Stop all Clui CC processes |
| `npm run build` | Production build (no packaging) |
| `npm run dist` | Package as macOS `.app` into `dist/` |
| `npm run doctor` | Run environment diagnostic |

## Troubleshooting

For setup issues, see [`docs/TROUBLESHOOTING.md`](docs/TROUBLESHOOTING.md) or run:

```bash
npm run doctor
```

## Credits

- **Original project:** [Clui CC](https://github.com/lcoutodemos/clui-cc) by [@lcoutodemos](https://github.com/lcoutodemos)
- **Custom features:** [@okjpg](https://github.com/okjpg)
- **License:** [MIT](LICENSE) (same as original)

## Tested On

| Component | Version |
|-----------|---------|
| macOS | 15.x (Sequoia) |
| Node.js | 20.x LTS, 22.x |
| Python | 3.12 (with setuptools installed) |
| Electron | 33.x |
| Claude Code CLI | 2.1.71 |

## License

[MIT](LICENSE)
