# Traffic Light FSM Controller with Pedestrian Crosswalk Logic

This project implements a finite state machine (FSM) traffic light controller for a North-South and East-West intersection with pedestrian crosswalk request handling. The design was created in Verilog and simulated in Vivado 2024.2.

## Project Overview

The controller manages normal traffic flow between North-South and East-West directions while allowing pedestrian requests to interrupt the normal cycle at the next safe transition point. The system uses a Moore machine, meaning the outputs are determined by the current state.

The final design uses six states:

- North-South green
- North-South yellow
- East-West green
- East-West yellow
- Crosswalk state after North-South traffic
- Crosswalk state after East-West traffic

Red lights are derived using combinational logic when a direction is not green or yellow.

## Key Features

- Verilog finite state machine design
- Moore machine implementation
- Pedestrian button request handling
- Persistent pedestrian request signal
- Moment-based timing transition signals
- Top-level module connecting the clock generator and FSM
- Vivado testbench simulation
- Five-bit light output encoding for North-South lights, East-West lights, and crosswalk signal

## Design Improvements

During simulation, the original continuously running clock signals caused some timing intervals to become inconsistent. To fix this, the design was updated to use moment-based transition signals that only trigger state changes when the green, yellow, or crosswalk timing signal reaches the correct transition point.

Another issue was that the pedestrian button would only be detected if it was pressed exactly when the FSM checked it. This was fixed by adding a persistent pedestrian request signal that stays active until the system reaches the crosswalk state.

## Simulation Results

The final simulation showed that the controller:

- Initializes correctly after reset
- Cycles through normal North-South and East-West traffic states
- Stores pedestrian requests until they can be safely served
- Activates the crosswalk state at the next appropriate transition
- Returns to normal traffic operation after the crosswalk interval

## Tools Used

- Verilog
- Vivado 2024.2
- FSM design
- Digital logic simulation
- Testbench verification

## Full Writeup

[View the full PDF writeup](writeup/Traffic_Light_FSM_Controller_Writeup.pdf)

## Future Improvements

Potential improvements include adding protected left-turn states and activating only the specific requested crosswalk instead of enabling all pedestrian crossings at once.

## Contributors

- Teremun Beard
- Perry Flagg
- Gideon Drury

## Repository Maintainer

Teremun Beard  
Electrical and Computer Engineering  
Worcester Polytechnic Institute
