# `.ai/` — geteilter Kontext für Claude, Codex und Gemini

Diese Verzeichnisstruktur ist die **Source of Truth** für alle drei
AI-Tools. Inhalte werden hier einmal gepflegt und von den jeweiligen
Einstiegsdateien (`CLAUDE.md`, `AGENTS.md`, `GEMINI.md`) im Repo-Root
referenziert.

## Struktur

```
.ai/
├── company.md      Firmen-/Marken-Infos, Tonalität, Glossar
├── context.md      Projekt-/Tech-Kontext, Konventionen
├── skills/         Wiederverwendbare Skills (SKILL.md je Skill-Ordner)
└── commands/       Slash-Command-Definitionen (Markdown je Command)
```

## Wie die Tools darauf zugreifen

| Tool         | Einstieg     | Mechanismus                              |
|--------------|--------------|------------------------------------------|
| Claude Code  | `CLAUDE.md`  | `@.ai/<datei>` (native Import-Syntax)    |
| Codex        | `AGENTS.md`  | Markdown-Referenzen auf `.ai/<datei>`    |
| Gemini CLI   | `GEMINI.md`  | `@./.ai/<datei>` (Import-Syntax)         |

Außerdem zeigen Symlinks in `.claude/`, `.codex/`, `.gemini/` auf
`.ai/skills` und `.ai/commands`, damit jedes Tool sie unter dem von
ihm erwarteten Pfad findet.

## Pflege

- **Niemals** Inhalte in `.claude/`, `.codex/` oder `.gemini/` direkt
  bearbeiten, wenn sie über Symlinks aus `.ai/` kommen.
- Neue Skills/Commands immer in `.ai/skills/` bzw. `.ai/commands/`
  anlegen.
- Tool-spezifische Eigenheiten (z. B. Claude-Skill-Frontmatter) sind
  okay; andere Tools ignorieren unbekannte Felder.
