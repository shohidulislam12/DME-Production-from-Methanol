# 🧪 Dimethyl Ether (DME) Production from Methanol — Process Simulation

A comprehensive **process flowsheet simulation** for the catalytic dehydration of methanol to produce **Dimethyl Ether (DME)**, developed using **COFE (CAPE-OPEN Flowsheet Environment)** and **ChemSep**.

![COFE](https://img.shields.io/badge/Simulator-COFE-green)
![ChemSep](https://img.shields.io/badge/Separation-ChemSep-blue)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

# 📖 Table of Contents

- [Overview](#-overview)
- [Process Description](#-process-description)
- [Reaction](#-reaction)
- [Flowsheet](#-flowsheet)
- [Unit Operations](#-unit-operations)
- [Stream Results](#-stream-results)
- [Software Used](#-software-used)
- [How to Run](#-how-to-run)
- [Key Learnings](#-key-learnings)
- [References](#-references)
- [Author](#-author)
- [License](#-license)

---

# 🔬 Overview

Dimethyl Ether (DME) is a clean-burning and environmentally friendly fuel with growing industrial importance. It is widely used as:

- 🔥 LPG substitute for domestic cooking and heating
- 🚛 Clean diesel alternative with low NOx and soot-free combustion
- 🧴 Aerosol propellant replacing harmful CFCs
- 🏭 Intermediate chemical for olefins, gasoline, and hydrogen production

This project simulates the **catalytic dehydration of methanol** to produce DME using a **Plug Flow Reactor (PFR)** and a rigorous **distillation-based separation system**.

---

# ⚗️ Reaction

The primary reaction involved is:

```math
2CH_3OH \rightarrow CH_3OCH_3 + H_2O
```

### Reaction Characteristics

| Parameter | Value |
|---|---|
| Reaction Type | Catalytic Dehydration |
| Catalyst | γ-Al₂O₃ (Gamma Alumina) |
| Nature | Exothermic |
| Heat of Reaction | ΔH ≈ −23.4 kJ/mol |
| Operating Temperature | 250–400 °C |
| Operating Pressure | 10–15 bar |

---

# ⚙️ Process Description

The overall process consists of three major sections:

## 1️⃣ Feed Preparation Section

- Fresh methanol is mixed with recycled methanol.
- The mixed feed is pumped to reactor pressure (~1350 kPa).
- Heat integration is applied using a shell-and-tube heat exchanger.
- A trim heater raises the feed to reactor inlet temperature.

## 2️⃣ Reaction Section

- The heated methanol enters a **Plug Flow Reactor (PFR)**.
- Catalytic dehydration converts methanol into:
  - Dimethyl Ether (DME)
  - Water

## 3️⃣ Separation Section

The reactor effluent is cooled and separated using a **two-column distillation train**:

### Column 1 — DME Column
- Produces high-purity DME overhead product.

### Column 2 — Methanol Recovery Column
- Recovers unreacted methanol for recycle.
- Removes water as bottom wastewater stream.

---

# 🧩 Flowsheet

```text
Fresh Methanol
       │
       ▼
    Mixer ───► Pump ───► Heat Exchanger ───► Heater ───► PFR Reactor
       ▲                                                    │
       │                                                    ▼
Recycle Methanol ◄──── Methanol Recovery ◄──── Cooler ◄──── Valve
                                            │
                                            ▼
                                   DME Distillation Column
                                            │
                                   High Purity DME
```

> Replace this section with your actual flowsheet image:

```markdown
![Flowsheet](flowsheet.png)
```

---

# 🛠 Unit Operations

| Unit | Description | Function |
|---|---|---|
| **Mixer_1** | Feed Mixer | Combines fresh and recycle methanol |
| **Pump_2** | Centrifugal Pump | Raises feed pressure |
| **HeatExchanger_4** | Shell & Tube HX | Feed preheating using heat integration |
| **HeaterCooler_3** | Trim Heater | Raises feed to reactor temperature |
| **PFR_6** | Plug Flow Reactor | Catalytic dehydration reaction |
| **HeatExchanger_4 (1)** | Process HX | Energy recovery from reactor effluent |
| **HeaterCooler_3 (1)** | Cooler | Condenses reactor products |
| **Valve_10** | Expansion Valve | Pressure reduction before distillation |
| **ChemSep Column 1** | Distillation Column | DME purification |
| **ChemSep Column 2** | Distillation Column | Methanol recovery and recycle |

---

# 📊 Stream Results

| Stream | Pressure (kPa) | Temperature | Flow (kmol/h) | Methanol | Water | DME |
|---|---:|---:|---:|---:|---:|---:|
| 1 (Fresh Feed) | 100 | 298 K | 274.07 | 0.99 | 0.01 | 0 |
| 2 | 101.325 | 338.5 K | 91.36 | 0.9999 | 0.00007 | 0 |
| 3 | 100 | 308.3 K | 365.43 | 0.9925 | 0.0075 | 0 |
| 4 | 1350 | 308.5 K | 365.43 | 0.9925 | 0.0075 | 0 |
| 10 | 1350 | 308.5 K | 365.43 | 0.9925 | 0.0075 | 0 |
| 11 (Reactor Inlet) | 1051.17 | 351 K | 365.43 | 0.9925 | 0.0075 | 0 |
| 13 | 101.325 | 338.8 K | 1075 | 0.9850 | 0.0150 | 0 |
| 14 | 101.325 | 338.5 K | 91.36 | 0.9999 | 0.00007 | 0 |
| 15 (DME Product) | 101.325 | 339.0 K | 91.36 | 0.0299 | 0.0299 | 0.970 |

---
https://kommodo.ai/i/wGkd0GAo3bD3rS5UD8Ah
✅ **Simulation converged successfully with no errors reported.**

> Full stream data and convergence details are available inside the `.fsd` simulation file.

---

# 💻 Software Used

| Software | Purpose |
|---|---|
| **COCO Simulator (COFE)** | Process flowsheet simulation |
| **ChemSep LITE** | Rigorous distillation modeling |
| **TEA Property Package** | Thermodynamic calculations |
| **CORN** | Reaction package |

## Official Websites

- COCO Simulator → https://www.cocosimulator.org/
- ChemSep → https://www.chemsep.com/

---

# 🚀 How to Run

## Step 1 — Install COCO Simulator

Download and install:

```text
https://www.cocosimulator.org/index_download.html
```

Includes:
- COFE
- TEA
- CORN
- COUSCOUS

---

## Step 2 — Install ChemSep LITE

Download from:

```text
https://www.chemsep.com/downloads/index.html
```

---

## Step 3 — Clone Repository

```bash
git clone https://github.com/your-username/DME-Production-Simulation.git
cd DME-Production-Simulation
```

---

## Step 4 — Open Simulation

1. Launch **COFE**
2. Open `Flowsheet2-4.fsd`
3. Click **Solve (▶)**

---

# 🎯 Key Learnings

- Developed a complete chemical process flowsheet
- Solved recycle stream convergence problems
- Applied process heat integration techniques
- Modeled a Plug Flow Reactor (PFR)
- Performed rigorous distillation design using ChemSep
- Improved understanding of CAPE-OPEN based simulation
- Validated material and energy balances

---

# 📚 References

1. Turton, R., Shaeiwitz, J. A., Bhattacharyya, D., & Whiting, W. B. (2018). *Analysis, Synthesis, and Design of Chemical Processes* (5th ed.). Prentice Hall.

2. Bondiera, J., & Naccache, C. (1991). *Kinetics of methanol dehydration in dealuminated H-mordenite*. Applied Catalysis, 69(1), 139–148.

3. Azizi, Z., Rezaeimanesh, M., Tohidian, T., & Rahimpour, M. R. (2014). *Dimethyl ether: A review of technologies and production challenges*. Chemical Engineering and Processing, 82, 150–172.

4. Semelsberger, T. A., Borup, R. L., & Greene, H. L. (2006). *Dimethyl ether (DME) as an alternative fuel*. Journal of Power Sources, 156(2), 497–511.

5. COCO Simulator Documentation  
   https://www.cocosimulator.org/

6. ChemSep Documentation  
   https://www.chemsep.com/

7. Sinnott, R. K., & Towler, G. (2020). *Chemical Engineering Design* (6th ed.). Butterworth-Heinemann.

---

# 👨‍💻 Author

## MD. Shohidul Islam Sifat

Chemical Engineering Student | Process Simulation Enthusiast

- 🎓 Department of Chemical Engineering
- 🏫 Jashore University of Science and Technology
- 💼 MERN Stack & Process Simulation Learner

### Connect With Me

- LinkedIn: https://www.linkedin.com/in/shohidulislam200/
- GitHub:(https://github.com/shohidulislam12)

