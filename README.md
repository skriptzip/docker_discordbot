# <img src="https://cdn.prod.website-files.com/6257adef93867e50d84d30e2/66e3d80db9971f10a9757c99_Symbol.svg" height="32" style="vertical-align:middle; margin-right:8px;"/> Discord Bot Template

[![Docker](https://img.shields.io/badge/Docker-Ready-blue.svg)](https://docker.com)
[![Python](https://img.shields.io/badge/Python-3.11-green.svg)](https://python.org)
[![discord.py](https://img.shields.io/badge/discord.py-2.6.3-7289da.svg)](https://discordpy.readthedocs.io/)

A production-ready Discord bot with slash commands, colored logging, and Docker development workflow.

## ✨ Features

- 🚀 **Modern Slash Commands** - Discord's latest command system
- 🎨 **Colored Logging** - Beautiful console output with file rotation
- 🐳 **Docker Development** - Edit locally, run in container
- 📊 **Environment Configs** - Development/production/minimal modes
- 🔧 **Auto Setup** - Smart initialization and file copying

## 🚀 Quick Start

### Prerequisites
- [Docker](https://docker.com) & Docker Compose
- Discord Bot Token ([Create here](https://discord.com/developers/applications))

### Setup
```bash
git clone https://github.com/skriptzip/discordbot.git
cd discordbot

# Configure environment
cp .env.example .env
# Edit .env with your DISCORD_TOKEN

# Start bot
docker-compose up -d

# View logs
docker-compose logs -f
```

## 📁 Structure

```
discordbot/
├── bot/
│   ├── bot.py                  # Main bot file
│   ├── example_commands.py     # Example slash commands
│   ├── bot_logging/            # Colored logging system
│   └── requirements.txt        # Dependencies
├── data/                       # Persistent data (volume mapped)
│   └── logs/                   # Log files
├── docker-compose.yml          # Development environment
└── Dockerfile                  # Container build
```

## 🎯 Available Commands

| Command | Description |
|---------|-------------|
| `/ping` | Check bot latency |
| `/status` | Show bot statistics |
| `/hello` | Friendly greeting |
| `/serverinfo` | Server information |
| `/userinfo [user]` | User information |
| `/logtest` | Demonstrate colored logging (admin only) |

## 🔧 Development

### Adding Commands
Edit `bot/bot.py` or create new files:
```python
@app_commands.command(name="hello", description="Say hello")
async def hello_slash(interaction: discord.Interaction):
    await interaction.response.send_message("Hello!")

bot.tree.add_command(hello_slash)
```

### Environment Variables
```bash
DISCORD_TOKEN=your_token_here
LOG_ENVIRONMENT=production  # development/production/minimal
FORCE_COLOR=1              # Enable colored logs
```

### Managing Dependencies
1. Edit `bot/requirements.txt`
2. Rebuild: `docker-compose up --build -d`

## ℹ️ Logging

The bot features a comprehensive colored logging system:

- 🔍 **DEBUG** (cyan) - Detailed debugging info
- ℹ️ **INFO** (green) - General information
- ⚠️ **WARNING** (yellow) - Important notices
- ❌ **ERROR** (red) - Error conditions
- 🚨 **CRITICAL** (bright red) - Critical failures

### Viewing Logs
```bash
# Container logs (colored)
docker-compose logs -f

# File logs
tail -f ./data/logs/bot.log
tail -f ./data/logs/discord.log
```
