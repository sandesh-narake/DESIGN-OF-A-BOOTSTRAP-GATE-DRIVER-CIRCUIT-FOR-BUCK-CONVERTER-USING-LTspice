# Design of a Bootstrap Gate Driver Circuit for Buck Converter Using LTspice

**Project Code:** 26EE472  
**Academic Year:** 2026–2027 (B.Tech Final Year, Semester 07)  
**Institution:** Shri Guru Gobind Singhji Institute of Engineering and Technology, Vishnupuri, Nanded - 431606 (M.S.)  

---

## 📌 Overview

Power electronic converters are widely used for efficient energy conversion in modern electrical systems. High-speed switching devices in these converters require an effective gate driving technique to ensure reliable operation and minimal switching losses.

This project focuses on the **design, simulation, and performance analysis of a Bootstrap Gate Driver Circuit for a Synchronous Buck Converter using LTspice**. A bootstrap gate driver provides the necessary gate-to-source voltage for switching a high-side N-channel MOSFET ($S_1$) by utilizing a bootstrap capacitor ($C_{\text{boot}}$) and a bootstrap diode ($D_{\text{boot}}$). This generates a floating gate supply without requiring an bulky or expensive isolated power source, offering a compact, reliable, and cost-effective solution.

---

## 🎯 Objectives

* To understand the working principle of the synchronous DC-DC Buck Converter.
* To study the operation and charging/discharging dynamics of the bootstrap gate driver circuit.
* To analyze high-side MOSFET gate driving using bootstrap level-shifting technology.
* To evaluate the switching performance, voltage ripples, and overall converter operation.
* To validate the complete circuit design through LTspice simulation and performance analysis under varying operating conditions.

---

## 🏗️ System Architecture

### 1. Block Diagram Overview

![Block Diagram Overview](Block_Diagram_Overview.png)

**Figure 1:** Block Diagram of the Power Stage and Control & Driving Stage.

The system consists of two primary paths: the **Power Stage** and the **Control & Driving Stage**. The Power Stage handles the main power flow, while the Control & Driving Stage generates the control signals required to operate the power components.



### 2. Circuit Description
The circuit topology implemented in LTspice includes:
* **Main Power Supply ($V_s$):** Provides the fixed input DC voltage to the buck converter stage.
* **Auxiliary Power Supply ($V$):** Supplies low-voltage DC power ($V_{DD}$) to the gate driver IC and charges the bootstrap network.
* **Gate Driver IC:** Accepts complementary logic-level inputs ($\text{PWM\_HS\_IN}$ at pin $\text{HI}$ and $\text{PWM\_LS\_IN}$ at pin $\text{LI}$) and outputs gate drive signals ($\text{HO}$ for high-side and $\text{LO}$ for low-side).
* **Bootstrap Network:** Composed of diode $D_{\text{boot}}$, current-limiting resistor $R_{\text{boot}}$, and bootstrap capacitor $C_{\text{boot}}$ connected between pins $\text{HB}$ and $\text{HS}$. When the low-side switch $S_2$ conducts, the $\text{HS}$ node is pulled to ground, charging $C_{\text{boot}}$ through $D_{\text{boot}}$. When $S_2$ turns off and $S_1$ is commanded on, the charge on $C_{\text{boot}}$ provides the floating supply above the switching node voltage.
* **Switching & Gate Conditioning Stage:**
  * **High-Side MOSFET ($S_1$):** Driven via gate resistor $R_1$ and pull-down resistor $R_2$.
  * **Low-Side MOSFET ($S_2$):** Driven via gate resistor $R_3$ and pull-down resistor $R_4$.
* **LC Filter & Load Stage:** Filter inductor ($L$) and output capacitor ($C$) smooth the switched node waveform to deliver a regulated output voltage ($V_o$) across the load ($R$).

---

## 🛠️ Software & Tools Required

* **Simulator:** [LTspice](https://www.analog.com/en/resources/design-tools-and-calculators/ltspice-simulator.html) (by Analog Devices)
* **Key Components Modeled:**
  * Half-Bridge / High-Low Side Gate Driver IC
  * Power MOSFETs ($S_1, S_2$)
  * Fast-recovery / Schottky Bootstrap Diode ($D_{\text{boot}}$)
  * Passive filtering and gate conditioning networks ($L, C, R, C_{\text{boot}}, R_{\text{boot}}, R_1\text{–}R_4$)

---

## 🚀 Getting Started

1. **Install LTspice:** Download and install the latest version of LTspice on your system.
2. **Open the Simulation File:** Launch LTspice and open the project schematic file (`.asc`).
3. **Configure Parameters:** Verify the input DC source ($V_s$), auxiliary supply ($V_{DD}$), PWM switching frequency, and duty cycle ($D$) according to the desired output voltage:
   $$V_o = D \cdot V_s$$
4. **Run Simulation:** Click the **Run** button to execute the transient analysis and probe key nodes:
   * High-side gate-to-source voltage ($V_{HO} - V_{HS}$)
   * Bootstrap capacitor voltage ($V_{HB} - V_{HS}$)
   * Switching node voltage ($V_{HS}$)
   * Inductor current ($I_L$) and Output voltage ($V_o$)



---

## 📚 References

1. Z. Zhou, X. Ming, B. Zhang and Z. Li, "Design of novel bootstrap driver used in high power BUCK converter," *2009 IEEE 8th International Conference on ASIC*, Changsha, China, 2009.
2. W. Lin, S. Pan, J. Gong, Z. Lin, K. Dai and X. Zha, "Design Considerations of Bootstrap Gate Driver With Fault Mitigation for Si- and GaN-Based High-Current Converters," in *IEEE Transactions on Industrial Electronics*.
3. N. Salem, L. Almatrafi, B. Shigdar and B. Alaidaroos, "Analysis and Design of Various Types of DC-DC Converters: A Comprehensive Study," *2024 21st Learning and Technology Conference (L&T)*, Jeddah, Saudi Arabia, 2024.
