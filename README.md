# Voice Calibration Plugin

Teach AI to write and talk like you.

This plugin learns your personal writing style through a series of interactive writing prompts — micro-stories, opinions, casual messages, descriptions — then generates a reusable **voice profile** that any Agent Skills host can use to match your tone, vocabulary, and personality.

The skill follows the open [Agent Skills specification](https://agentskills.io). Codex, Cursor, Claude Code, Gemini CLI, GitHub Copilot, and other hosts can load the same `skills/voice-calibration/` folder.

## Installation

One command installs the skill for every agent it finds on your machine (Cursor, Codex, Claude Code, and the rest):

```bash
npx skills add raulpetruta/voice-calibration-plugin -g -y
```

That installs the skill for every agent the CLI finds. Some agents, such as PromptScript, reject a global install and print a failure for that one target. Codex, Cursor, Claude Code, and the others in the summary still receive the skill.

Or install for one agent:

```bash
npx skills add raulpetruta/voice-calibration-plugin -g -y -a cursor
npx skills add raulpetruta/voice-calibration-plugin -g -y -a codex
npx skills add raulpetruta/voice-calibration-plugin -g -y -a claude-code
```

`-g` installs it for all of your projects. Drop `-g` to install it only in the current project.

### Claude Code marketplace

In Claude Code:

```
/plugin marketplace add raulpetruta/voice-calibration-plugin
/plugin install voice-calibration-plugin@voice-calibration-marketplace
```

Restart Claude Code, then run `/voice-calibration-plugin:voice-calibration`.

### Cursor marketplace

```bash
cursor-agent plugin marketplace add https://github.com/raulpetruta/voice-calibration-plugin
```

In Cursor, run `/plugin`, open the marketplace, and install **voice-calibration-plugin**.

### Codex marketplace

```bash
codex plugin marketplace add raulpetruta/voice-calibration-plugin
codex plugin add voice-calibration-plugin@voice-calibration-marketplace
```

## Voice profile

Every host should read the same two files:

- **Project**: `.voice-profile.md` in the project root
- **Global**: `~/.agents/voice-profile.md`

Profiles already saved at `~/.claude/voice-profile.md` are still read until the next global save, which writes `~/.agents/voice-profile.md`.

## Usage

### Calibrate your voice

Run the `voice-calibration` skill, or say:

> "Learn my writing style"

The agent guides you through 6-12 writing prompts, analyzes your responses, and generates a voice profile.

### Write in your voice

Once your profile exists, ask:

> "Write an email to my team about the new feature — use my voice"

The agent reads your profile and matches your style.

### Update your profile

Run calibration again anytime. You can start fresh or add more samples to refine your existing profile.

## How it works

1. **Prompts** — The agent presents diverse writing exercises (stories, opinions, rants, explanations) to capture your style across different registers
2. **Analysis** — Your samples are analyzed across 7 dimensions: sentence structure, vocabulary, tone, punctuation, narrative style, conversational markers, and cultural markers
3. **Profile** — A structured voice profile is generated with specific observations, sample phrases, and anti-patterns to avoid
4. **Review** — You review and refine the profile before it's saved

## License

MIT — see [LICENSE](LICENSE) for details.
