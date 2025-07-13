# 🦄 Unicorn Adventure Game

A web-based Pac-Man style game featuring a cute unicorn character navigating through mazes, collecting coins, and avoiding intelligent enemies.

## 🎮 How to Play

1. **Launch**: Open `unicorn-game.html` in any modern web browser
2. **Controls**: Use Arrow Keys or WASD to move the unicorn
3. **Objective**: Collect all gold coins to advance to the next level
4. **Avoid**: Colored enemy squares that chase you with AI pathfinding
5. **Collect**: Hearts for bonus points and extra lives
6. **Timer**: Complete each level within 200 seconds

## 🎯 Game Mechanics

### Scoring System
- **Gold Coins**: 10 points each (required to complete level)
- **Hearts**: 50 points + 1 extra life
- **Level Completion**: 100 bonus points

### Difficulty Progression
- **Level 1**: 1 enemy, 15 coins
- **Each Level**: +1 enemy (max 6), +3 coins, +30% enemy speed

### Lives System
- Start with 3 lives
- Lose 1 life when touched by enemy or timer expires
- Gain lives by collecting hearts
- Game over when lives reach 0

## 🏗️ Code Structure

### HTML Structure
```
gameContainer
├── gameInfo (UI display)
└── gameCanvas (800x600 game area)
```

### JavaScript Architecture

#### 1. Game State Management
```javascript
gameState = {
    level, score, lives, timer, 
    gameRunning, levelComplete
}
```

#### 2. Game Objects
- **Unicorn**: Player character with position, size, speed, direction
- **Enemies**: AI-controlled with pathfinding toward unicorn
- **Collectibles**: Coins (required) and hearts (bonus)
- **Walls**: Static maze obstacles

#### 3. Core Systems

**Initialization Functions**:
- `createMaze()` - Generates wall layout
- `createCollectibles()` - Spawns coins and hearts
- `createEnemies()` - Creates AI enemies with scaling difficulty

**Movement & Physics**:
- `moveUnicorn()` - Player movement with wall collision
- `moveEnemies()` - AI pathfinding using distance calculations
- `isColliding()` - Rectangle collision detection

**Rendering Pipeline**:
- `drawWalls()` - Blue maze walls
- `drawUnicorn()` - Detailed unicorn with horn, eyes, mane
- `drawEnemies()` - Colored squares with eyes
- `drawCollectibles()` - Golden coins and pink hearts

**Game Logic**:
- `checkCollisions()` - Item collection and enemy contact
- `checkLevelComplete()` - Win condition verification
- `updateTimer()` - Countdown and time penalties

#### 4. Game Loop
```javascript
gameLoop() {
    updateTimer()
    moveUnicorn()
    moveEnemies()
    checkCollisions()
    checkLevelComplete()
    renderAll()
    requestAnimationFrame(gameLoop)
}
```

## 🎨 Visual Design

### Graphics System
- **Canvas Size**: 800x600 pixels for optimal web display
- **High-Definition**: Detailed sprites with multiple colors/layers
- **Unicorn Design**: Pink body, gold horn, hot pink mane, black eyes
- **Enemy Design**: Colorful squares with white/black eyes
- **Collectibles**: Layered gold coins, heart-shaped power-ups

### UI Elements
- Real-time display of level, score, lives, timer
- Game over overlay with final score
- Gradient background with glassmorphism effects

## 🤖 AI System

### Enemy Intelligence
```javascript
// Calculate direction to unicorn
dx = unicorn.x - enemy.x
dy = unicorn.y - enemy.y
distance = sqrt(dx² + dy²)

// Move toward unicorn
moveX = (dx / distance) * enemy.speed
moveY = (dy / distance) * enemy.speed
```

Enemies use direct pathfinding to chase the unicorn, with collision detection preventing movement through walls.

## 📊 Game Flow Diagram

```
Start Game
    ↓
Initialize Level
    ↓
Game Loop ←─────────┐
    ├─ Move Player  │
    ├─ Move Enemies │
    ├─ Check Items  │
    ├─ Check Timer  │
    └─ Render All   │
    ↓               │
Level Complete? ────┘
    ↓ (Yes)
Next Level
    ↓
All Lives Lost?
    ↓ (Yes)
Game Over
```

## 🔧 Technical Features

- **HTML5 Canvas** for smooth 2D graphics
- **RequestAnimationFrame** for 60fps gameplay
- **Event-driven input** with keyboard state tracking
- **Collision detection** using AABB (Axis-Aligned Bounding Box)
- **Procedural generation** for collectible placement
- **Responsive design** with CSS flexbox layout

## 🚀 Browser Compatibility

- Chrome/Edge 60+
- Firefox 55+
- Safari 12+
- Mobile browsers (touch controls not implemented)

## 📝 File Structure

```
unicorn-game.html    # Complete game (HTML + CSS + JavaScript)
README.md           # This documentation
```

The game is entirely self-contained in a single HTML file for easy deployment and sharing.