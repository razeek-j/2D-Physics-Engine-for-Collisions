# 2D Physics Engine for Collisions

## Project Overview
This project implements a 2D physics engine in a Jupyter Notebook to simulate the motion and collisions of multiple balls. The simulation incorporates object-oriented programming (OOP) principles, mathematical equations for motion and collisions, and visualization using Matplotlib animations. The goal is to model realistic physical interactions, including gravity, friction, elastic collisions, and inelastic collisions, while visualizing the dynamic behavior of the system.

Demo video: https://youtu.be/tr6TcoolEFA 

## Objectives
- **OOP Requirements**: Define a `Ball` class with attributes like position, velocity, mass, radius, and color, and methods for updating positions and handling collisions.
- **Math Requirements**: Implement equations of motion under gravity and friction, and resolve collisions using momentum conservation and the coefficient of restitution.
- **Visualization**: Use Matplotlib to animate the motion and collisions of balls in a 2D space.

## Simulation Parameters
The simulation uses the following key constants:
- **Coefficient of Restitution (e)**: Determines the elasticity of collisions.
    - `e = 1`: Perfectly elastic collisions.
    - `0 < e < 1`: Partially inelastic collisions.
    - `e = 0`: Perfectly inelastic collisions (objects may stick together or lose all relative velocity along the collision normal).
    *Special rule: Red-green ball collisions have `e = 0.0`.*
- **Gravity**: -9.8 m/s², acting downward to simulate realistic falling motion.
- **Friction**: A damping factor of 0.995 applied to velocities to simulate energy loss due to air resistance or surface friction.
- **Time Step (DT)**: 0.05 seconds, controlling the simulation's temporal resolution.
- **Electrostatic Constant**: `3.0` (can be adjusted to vary repulsive force strength between balls).

## Key Features
- **Object-Oriented Design**: The `Ball` class encapsulates properties (position, velocity, mass, radius, color) and behaviors (update position, check wall/ball collisions, resolve collisions, apply repulsion).
- **Collision Physics**:
    - **Collision Detection**: Uses the Euclidean distance between ball centers and their radii.
    - **Collision Resolution**: Implements momentum conservation and the coefficient of restitution.
    - **Overlap Resolution**: Prevents balls from "sticking" or tunneling by symmetrically adjusting positions based on their overlap, with a small epsilon for numerical separation.
- **Electrostatic Repulsion**: Balls exert a repulsive force on each other, simulated using an electrostatic-like force inversely proportional to the square of the distance.
- **Wall Collisions**: Balls interact with the boundaries of the simulation space (10x10 units).
- **Visualization**:
    - Uses Matplotlib for plotting and `FuncAnimation` for animating the balls' motion.
    - Each ball is represented by a `plt.Circle` patch.
- **Stopping Condition**: The animation can stop if all balls come to a near standstill (velocity threshold < 0.1 units/second) to save computational resources.

## How to Run
1.  Ensure you have Python installed.
2.  Install the necessary libraries:
    ```bash
    pip install numpy matplotlib ipython
    ```
3.  Download the `2D_Physics_Engine_For_Collisions.ipynb` file.
4.  Open and run the Jupyter Notebook in an environment like Jupyter Lab or Jupyter Notebook.
    ```bash
    jupyter lab 2D_Physics_Engine_For_Collisions.ipynb
    ```
    or
    ```bash
    jupyter notebook 2D_Physics_Engine_For_Collisions.ipynb
    ```
5.  Execute the cells in the notebook sequentially. The animation will be displayed inline.

## Libraries Used
- **NumPy**: For efficient numerical computations, vector operations, and distance calculations.
- **Matplotlib**: For creating plots and animations to visualize the balls' motion.
- **IPython.display.HTML**: Used for embedding the animation (though the primary animation uses `%matplotlib notebook`).
- **Random**: To generate random initial conditions for the balls (position, velocity, radius, color).

## Simulation Setup
- **World Dimensions**: 10x10 unit square.
- **Number of Balls**: 20 balls are initialized with random properties:
    - **Radius**: Randomly chosen between 0.2 and 0.5 units.
    - **Mass**: Proportional to radius (mass = radius * 2).
    - **Position**: Randomly placed within the world boundaries.
    - **Velocity**: Random initial velocities between -2 and 5 units/second in both x and y directions.
    - **Color**: Randomly selected from a predefined list (`['red', 'blue', 'green', 'purple', 'orange', 'cyan']`).
