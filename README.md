# MIPS Single-Cycle Processor in VHDL 💻

## Introduction

This repository contains the **VHDL** implementation of a **Single-Cycle MIPS Processor**. The architecture is based on the fundamental principles of Computer Architecture, designed to execute a subset of the MIPS Instruction Set Architecture (ISA) in a single clock cycle.

This project is ideal for students and enthusiasts looking to understand the hardware description of a basic RISC-based CPU, including the major components like the Instruction Fetch, Decode, Execute, and Memory access stages.

---

## 🏗️ Architecture & Modules

The MIPS processor is divided into several interconnected VHDL entities (modules) that represent the core functional units of a CPU pipeline, albeit simplified for a single-cycle design.

### Key Modules

| File | Description |
| :--- | :--- |
| **`mips_single_cycle_top.vhd`** | (Implied/Placeholder for the top-level entity) The main entity connecting all sub-modules. |
| **`inst_fetch.vhd`** | **Instruction Fetch (IF):** Contains the Program Counter (PC) and logic to fetch the next instruction from the Instruction Memory (RAM). |
| **`instr_decode.vhd`** | **Instruction Decode (ID):** Logic to parse instruction fields (OpCode, registers, immediate values) and generate control signals. |
| **`reg_file.vhd`** | The **Register File:** A memory component for storing and retrieving the 32 general-purpose MIPS registers. |
| **`control_unit.vhd`** | The **Main Control Unit:** Generates all necessary control signals for the datapath based on the instruction's opcode. |
| **`exec_unit.vhd`** | **Execution Unit (EX):** Includes the ALU (Arithmetic Logic Unit) for performing arithmetic and logical operations, and branching logic. |
| **`mem_unit.vhd`** | **Memory Access (MEM):** Handles data read/write operations to the Data Memory (RAM). |
| **`ram.vhd`** | **RAM Module:** The shared memory component used for both instruction and data storage. |

### Auxiliary Files

* `mono_pulse_gener.vhd`: Utility for generating clock/single pulses, often used for manual stepping or debouncing on a physical board.
* `seven_seg_disp.vhd`, `seven_seg_display.vhd`: Logic for driving a **seven-segment display**, likely for debugging or displaying register contents/program output on an FPGA.
* `test_env.vhd`: A **Testbench** for simulation and verification of the top-level entity.

---

## ⚙️ Getting Started

### Prerequisites

To synthesize or simulate this project, you will need a VHDL development environment:

1.  A VHDL compiler/simulator (e.g., **ModelSim**, **GHDL**, or the simulator integrated into an FPGA vendor's IDE like **Xilinx Vivado** or **Intel Quartus**).
2.  Basic understanding of the **MIPS ISA** (Instruction Set Architecture).

---

## 🚀 Usage and Simulation

### Simulation

1.  Load all `.vhd` files into your VHDL simulator.
2.  Compile the files in the correct dependency order.
3.  Run the **`test_env`** entity as the top-level module to start the simulation.
4.  Observe the signals in the waveform viewer, specifically the PC, Instruction, ALU result, and Register File contents, to verify correct execution of the test program (found in `MIPS_Single-cycle.txt` or embedded in the testbench).

### Synthesis (FPGA Deployment)

This design is structured for synthesis. If targeting a specific FPGA board (e.g., **Basys 3**, **Nexys A7**), you will need to:

1.  Set the **Top-Level Entity** in your IDE (likely a custom wrapper that includes the seven-segment display logic).
2.  Define the necessary **Pin Constraints** (`.xdc` or `.qsf` file) for the clock, reset, switches, and the seven-segment display outputs.
3.  Run Synthesis and Implementation.

---

## 🖼️ Included Diagrams

The repository includes visual aids to help understand the processor's structure:

* `Instruction_Fetch.png`: Diagram illustrating the **Instruction Fetch** pipeline stage.
* `instruction_decode.png`: Diagram illustrating the **Instruction Decode** and Register Read stages.
