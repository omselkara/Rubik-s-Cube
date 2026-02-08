# 3D Rubik's Cube Simulator

An interactive 3D Rubik's Cube simulator built with Processing. This project allows you to manipulate a virtual Rubik's Cube in 3D space, scramble it, and solve it using an automated solver.

## 🎯 Features

- **3D Visualization**: Fully rendered 3D Rubik's Cube with realistic colors
- **Interactive Controls**: Rotate the cube view with mouse and perform moves with keyboard
- **Cube Manipulation**: Execute standard Rubik's Cube moves (F, R, U, B, L, D and their inverses)
- **Scramble Function**: Automatically scramble the cube with 100 random moves
- **Auto-Solver**: Built-in solver that can automatically solve the cube by reversing the move history
- **Smooth Animations**: Watch the cube rotate smoothly as you perform moves
- **Score Tracking**: Internal scoring system to track how many pieces are in the correct position

## 📋 Prerequisites

Before running this project, you need to have Processing installed on your system.

### Installing Processing

1. Download Processing from the [official website](https://processing.org/download)
2. Choose the version appropriate for your operating system (Windows, macOS, or Linux)
3. Extract the downloaded file and run the Processing IDE

**Supported Versions**: Processing 3.x or later

## 🚀 Getting Started

### Installation

1. Clone this repository:
```bash
git clone https://github.com/omselkara/Rubik-s-Cube.git
```

2. Navigate to the project directory:
```bash
cd Rubik-s-Cube
```

3. Open the project in Processing:
   - Launch Processing IDE
   - Go to File → Open
   - Navigate to the project folder and select `rubik_cube3d.pde`

### Running the Project

1. Click the "Run" button (▶️) in the Processing IDE, or press `Ctrl+R` (Windows/Linux) or `Cmd+R` (macOS)
2. A window will open displaying the 3D Rubik's Cube

## 🎮 Controls

### Mouse Controls
- **Click and Drag**: Rotate the camera view around the cube
  - Horizontal drag: Rotate around Y-axis
  - Vertical drag: Rotate around X-axis

### Keyboard Controls

#### Cube Face Rotations
The keyboard is divided into two rows for clockwise and counter-clockwise rotations:

**Clockwise Rotations:**
- `Q` - Front face clockwise
- `W` - Right face clockwise
- `E` - Up face clockwise
- `R` - Back face clockwise
- `T` - Left face clockwise
- `Y` - Down face clockwise

**Counter-Clockwise Rotations:**
- `A` - Front face counter-clockwise
- `S` - Right face counter-clockwise
- `D` - Up face counter-clockwise
- `F` - Back face counter-clockwise
- `G` - Left face counter-clockwise
- `H` - Down face counter-clockwise

#### Additional Controls
- `SPACE` - Toggle auto-solve mode (automatically solves the cube by reversing all moves)
- `-` (Minus) - Scramble the cube with 100 random moves

## 🏗️ Project Structure

The project consists of four main Processing files:

### `rubik_cube3d.pde` (Main File)
The main sketch file that:
- Initializes the cube and rendering environment
- Handles the main draw loop
- Manages user input (mouse and keyboard)
- Controls the solve functionality

**Key Variables:**
- `n`: Size multiplier for the cube (default: 50)
- `speed`: Animation speed for rotations (default: 15, max: 90)
- `anglex`, `angley`: Current camera rotation angles

### `cube.pde` (Cube Logic)
Contains the core Rubik's Cube implementation:

**`rubik_cube` Class:**
- `map[6][3][3]`: 3D array storing the color state of all 54 stickers
- `show()`: Renders the cube in 3D space
- `move()`: Executes a rotation move
- `getscore()`: Calculates how many pieces are in correct positions
- `scramble()`: Randomizes the cube state

**`cube()` Function:**
- Renders individual cubes with specified colors and transformations
- Handles rotation transformations for animated moves

### `matrix.pde` (3D Mathematics)
Mathematical functions for 3D transformations:
- `matrixmul()`: Matrix multiplication for transformations
- `rotatex()`: Rotation around X-axis
- `rotatey()`: Rotation around Y-axis
- `rotatez()`: Rotation around Z-axis

### `sketch.properties`
Configuration file specifying the main sketch file.

## 🎨 Color Scheme

The cube uses the standard Rubik's Cube color scheme:
- **White** (255, 255, 255) - Face 0
- **Yellow** (255, 255, 0) - Face 1
- **Green** (88, 213, 104) - Face 2
- **Blue** (28, 95, 254) - Face 3
- **Orange** (255, 175, 28) - Face 4
- **Red** (237, 48, 48) - Face 5
- **Black** (0, 0, 0) - Hidden/inner faces

## 🔧 Customization

You can modify the following parameters in `rubik_cube3d.pde`:

- **Cube Size**: Change the `n` variable (line 3) to make the cube larger or smaller
- **Animation Speed**: Modify the `speed` variable (line 5) to make rotations faster or slower (1-90)
- **Window Size**: Update the `size(600, 600, P3D)` in `setup()` to change window dimensions
- **Frame Rate**: Adjust `frameRate(60)` in `setup()` to change animation smoothness

## 🧠 How It Works

### Cube State Representation
The cube state is stored in a 3D array `map[6][3][3]` where:
- First dimension (6): Represents the 6 faces of the cube
- Second dimension (3): Represents rows on each face
- Third dimension (3): Represents columns on each face

### Move Execution
When a move is executed:
1. The animation flag is set with the move type
2. Each frame, the affected layer rotates by `speed` degrees
3. After 90° rotation, the internal state array is updated to reflect the new sticker positions
4. Move is recorded in the move history for potential solving

### Auto-Solve Algorithm
The solver uses a simple but effective approach:
1. Records every move made by the user
2. When solve mode is activated, performs the inverse of each move in reverse order
3. This guarantees a solution if the cube was scrambled using only the interface

## 🤝 Contributing

Contributions are welcome! Here are some ways you can contribute:

1. **Bug Reports**: If you find a bug, please create an issue with details
2. **Feature Requests**: Have an idea for improvement? Open an issue to discuss it
3. **Code Contributions**: 
   - Fork the repository
   - Create a feature branch (`git checkout -b feature/AmazingFeature`)
   - Commit your changes (`git commit -m 'Add some AmazingFeature'`)
   - Push to the branch (`git push origin feature/AmazingFeature`)
   - Open a Pull Request

### Ideas for Future Improvements
- Implement standard Rubik's Cube solving algorithms (CFOP, Roux, etc.)
- Add timer functionality for speedcubing practice
- Include move counter display
- Add different cube sizes (2x2, 4x4, etc.)
- Implement a tutorial mode for beginners
- Add texture or lighting effects for better visualization
- Export/import cube states
- Multiplayer mode for solving competitions

## 📝 License

This project is open source and available for educational and personal use.

## 👨‍💻 Author

**omselkara**
- GitHub: [@omselkara](https://github.com/omselkara)

## 🙏 Acknowledgments

- Built with [Processing](https://processing.org/), an open-source graphical library and IDE
- Inspired by the classic Rubik's Cube puzzle invented by Ernő Rubik in 1974

## 📞 Support

If you encounter any issues or have questions:
1. Check the Issues page to see if your problem has been reported
2. Create a new issue with detailed information about the problem
3. Include steps to reproduce the issue if applicable

---

**Enjoy playing with the virtual Rubik's Cube! 🎲**
