# Mago Config

My Mago config for Mago 1.9.0+.

Clone this repository to `~/.config/mago`

For formatting in VSCode, `jkillian.custom-local-formatters` extension is recommended. You may need to use a wrapper shell script to enable custom config in Mago:

```json
"customLocalFormatters.formatters": [
  {
    // "command": "mago format --stdin-input", // this is the default command without custom config
    "command": "\"$HOME/.local/bin/mago-vscode-format\"",
    "languages": ["php"]
  }
]
```

Create a wrapper shell script

```zsh
mkdir -p "$HOME/.local/bin"

cat > "$HOME/.local/bin/mago-vscode-format" <<'SH'
#!/usr/bin/env bash
set -euo pipefail

exec mago --config "$HOME/.config/mago/mago.toml" format --stdin-input
SH

chmod +x "$HOME/.local/bin/mago-vscode-format"
```

For more information see:

- [Mago](https://mago.carthage.software/)
- [VSCode marketplace for Custom Local Formatters](https://marketplace.visualstudio.com/items?itemName=jkillian.custom-local-formatters)
