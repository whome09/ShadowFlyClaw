[### ShadowFlyClaw Plugin Wiki (English)

------

### 1. Overview

**ShadowFlyClaw** is a high-performance grappling hook plugin that allows players to launch a grapple using a fishing rod for rapid movement. Key features:

- **Particle Effects**: Cyan particle trail (configurable)
- **Cooldown System**: Prevents spamming (default: 2 seconds)
- **Range Limiter**: Max 50-block distance (configurable)
- **Debug Mode**: Real-time parameter display
- **Localization Support**: Fully customizable messages

------

### 2. Commands

|   Command   |   Aliases    |       Permission       |       Description       |
| :---------: | :----------: | :--------------------: | :---------------------: |
| `/gethook`  |    `/sfc`    |          None          | Get grappling hook item |
| `/ghreload` | `/sfcreload` | `shadowflyclaw.reload` |  Reload configuration   |
| `/ghdebug`  | `/sfcdebug`  | `shadowflyclaw.debug`  |    Toggle debug mode    |

> 📌 Example: `/sfcget` gives a fishing rod named **"&6ShadowFlyClaw Launcher"**

------

### 3. Permissions

|    Permission Node     | Default |      Function       |
| :--------------------: | :-----: | :-----------------: |
| `shadowflyclaw.reload` |   OP    | Allows `/sfcreload` |
| `shadowflyclaw.debug`  |   OP    | Allows `/sfcdebug`  |

------

### 4. Configuration File (`config.yml`)


```yaml
hook:
  cooldown: 2.0     # Cooldown (seconds)
  max-distance: 50.0 # Max range (blocks)
  velocity: 2.7      # Launch speed
  item:
    name: "&6ShadowFlyClaw Launcher" # Item name
    lore:                            # Item description
      - "&7Right-click to launch grapple"
      - "&8Cooldown: &7{cooldown}s"  # {cooldown} auto-replaces
  particle:
    color: "#00FFFF" # Particle color (HEX)
  debug: false       # Global debug switch (reserved)

messages: # Fully customizable
  commands:
    get-hook: "&aYou received a &6ShadowFlyClaw Launcher&a!"
    reload: "&aConfiguration reloaded!"
    no-permission: "&cYou don't have permission for this command!"
    player-only: "&cOnly players can use this command!"
  usage:
    cooldown: "&cCooldown: &6{cooldown}s"
    no-target: "&cNo valid target found!"
    out-of-range: "&cOut of range! ({distance} > {max-distance})"
    success: "&aGrapple launched successfully!"
  debug:
    enabled: "&eDebug mode enabled!"
    disabled: "&7Debug mode disabled."
    info: "&7Distance: &f{distance} &7| Velocity: &f{velocity} &7| Cooldown: &f{cooldown}s"
```

------

### 5. Core Mechanics

#### **Grapple Workflow**

1. **Activation**
   Right-click air/block with the hook item
2. **Target Detection**
   Scans for first ​**solid block**​ within 50 blocks
3. **Validation Checks**:•Cooldown status•Target within range•Valid target exists
4. **Movement Execution**
   Pulls player toward target center at `2.7` velocity
5. **Effects**:•Cyan particle trail (player → target)•`ENTITY_FISHING_BOBBER_THROW` sound

#### **Debug Mode**

Enable with `/sfcdebug` to display:


```markdown
Distance: 32.5 | Velocity: 2.7 | Cooldown: 2.0s
```

on each grapple use.

------

### 6. Messages System

All messages support:

- **Color Codes**: `&` prefix (e.g., `&c` = red)
- **Dynamic Placeholders**:•`{cooldown}` → Current cooldown•`{distance}` → Actual distance•`{max-distance}` → Max range•`{velocity}` → Launch speed
](https://github.com/whome09/ShadowFlyClaw)
