# self-driving-car-simulation-python

<img width="1465" height="836" alt="Screenshot 2026-04-01 131733" src="https://github.com/user-attachments/assets/a263d52c-a38e-48df-950b-2ea9438a5d8e" />


Implemented various sensors and car mechanics with math.

Autonomous Maze-Solving Car with Reinforcement Learning

A high-performance Pygame simulation featuring a car agent equipped with LIDAR-like raycasting sensors navigating through a procedurally generated or manually defined maze. 

This environment is specifically designed for training Reinforcement Learning (RL) models or Genetic Algorithms (like NEAT).
🚀 Features
Real-Car Physics: Implements weight, friction, and momentum-based movement. The car only turns when moving, simulating real-world steering geometry.

Raycasting Sensor Suite: An 8-ray LIDAR system that detects distances to walls in real-time, providing the "Vision" for the AI agent.

Procedural Maze Generation: Uses a Randomized Depth-First Search (DFS) algorithm to create unique, complex layouts every session.

Data-Driven Navigation: All wall positions are stored in a high-speed numpy array (wallNp), allowing for efficient collision detection and mathematical ray-line intersection.

High-Fidelity Visuals: Dark-mode UI with "Neon" orange-trimmed walls inspired by professional micromouse competition mazes.

🛠️ Technical Architecture1. Sensor System (Observation Space)The car emits rays across a 180° Field of View (FOV). 

Each ray calculates the intersection point with the nearest wall segment using the formula:
$$d = \frac{(x_4-x_3)(y_1-y_3) - (y_4-y_3)(x_1-x_3)}{(y_4-y_3)(x_2-x_1) - (x_4-x_3)(y_2-y_1)}$$

These distances are normalized and fed as inputs to the neural network.

2. Physics & CollisionsFriction: Simulated via a velocity decay coefficient ($v = v \cdot 0.92$).

Collision Resolution: Point-to-segment distance checking prevents the car from phasing through walls or leaving the frame boundaries.
Reward Function Design:Penalty: -100 for wall collisions.Reward: +Distance_Delta for moving closer to the goal.
Bonus: +500 for reaching the center finish zone.
📦 InstallationClone the repo:Bashgit clone https://github.com/yourusername/autonomous-maze-car.git
Install dependencies:Bashpip install pygame numpy
Run the simulation:Bashpython main.py
📝 LicenseDistributed under the MIT License. See LICENSE for more information.Author: [Your Name/Handle]Project: AI Research - Autonomous Systems 2026
