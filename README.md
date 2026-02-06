# RIS-Assisted V2V ISAC Channel Modeling and Learning Framework

This repository provides the simulation codes, statistical modeling modules, and learning-based enhancement algorithms for the paper:

**"Deep-Learning-Driven Non-Stationary 3D Channel Modeling for RIS-Assisted V2V Integrated Sensing and Communications"**

The project develops a physics-based geometric stochastic channel model (GBSM) for RIS-assisted vehicle-to-vehicle (V2V) integrated sensing and communications (ISAC) systems, and further incorporates a supervised learning-based MLP neural network to enhance channel statistic prediction accuracy and reduce computational complexity.

---

## 📌 Key Features

### Physics-Based Channel Modeling
- 3D non-stationary geometric stochastic channel model
- LoS / NLoS / VLoS propagation mechanisms
- Hybrid near-field and far-field modeling
- Explicit RIS reflection amplitude and phase embedding
- Time-varying mobility of Tx, Rx, and RIS

### Statistical Characterization
The framework analytically derives:
- Spatial cross-correlation functions (CCFs)
- Temporal auto-correlation functions (ACFs)
- Frequency correlation functions (FCFs)

The impacts of:
- antenna spacing  
- RIS array size  
- RIS phase configuration  
- mobility and Doppler  
are thoroughly investigated.

### Learning-Based Enhancement
- Supervised MLP neural network
- Multi-physical feature inputs
- Dynamic noise perturbation strategy
- Fast prediction of channel statistics
- Reduced computational overhead compared to full theoretical evaluation

---

## 📂 Repository Structure
│── main_simulation/ # Main scripts for channel simulations
│── channel_model/
│ ├── LoS/
│ ├── NLoS/
│ ├── RIS/
│ └── statistical_functions/
│
│── learning_module/
│ ├── dataset_generation/
│ ├── mlp_training/
│ └── prediction/
│
│── results/
│ ├── CCF/
│ ├── ACF/
│ ├── FCF/
│ └── figures/
│
│── utils/
│── README.md

---

## ⚙️ Requirements

- MATLAB R2021b or later
- Deep Learning Toolbox
- Parallel Computing Toolbox (optional for acceleration)

---

## 🚀 Quick Start

### 1️⃣ Channel Simulation
Run:

```matlab
main_simulation_ccf.m
main_simulation_acf.m
main_simulation_fcf.m
This will generate:

theoretical CCF / ACF / FCF curves

RIS size comparison results

sensing vs communication statistics
2️⃣ Dataset Generation
generate_training_dataset.m
rho_CCF_*.fig
rho_ACF_*.fig
rho_FCF_*.fig
These files serve as ground-truth labels for neural network training.

3️⃣ Train MLP Model
main_train_mlp_multi_input_dynamic.m


Includes:

multi-dimensional physical features

normalization

adaptive sampling

performance evaluation (RMSE / MAE / R²)

4️⃣ Prediction & Comparison
main_predict_and_compare.m


Generates:

theoretical vs predicted curves

error metrics

visualization plots

🧠 Methodology Overview
Channel Modeling

The RIS reflection coefficient of each element is modeled as

𝜒
𝑚
𝑥
,
𝑚
𝑧
(
𝑡
)
𝑒
𝑗
𝜙
𝑚
𝑥
,
𝑚
𝑧
(
𝑡
)
χ
m
x
	​

,m
z
	​

	​

(t)e
jϕ
m
x
	​

,m
z
	​

	​

(t)

which directly influences the spatio-temporal channel responses via

𝑒
𝑗
(
𝜙
(
𝑡
)
−
𝜙
(
𝑡
+
Δ
𝑡
)
)
e
j(ϕ(t)−ϕ(t+Δt))

This phase-difference term explicitly affects:

spatial CCFs

temporal ACFs

propagation non-stationarity

Larger RIS dimensions introduce stronger phase diversity, resulting in faster correlation decay.

Learning Enhancement

The MLP learns the nonlinear mapping:

Physical Parameters
→
Statistical Channel Metrics
Physical Parameters→Statistical Channel Metrics

Advantages:

avoids repeated integral computations

accelerates simulations

preserves physical interpretability

suitable for real-time system design

📊 Example Results

Typical observations:

spatial correlations decay with antenna spacing

temporal ACFs show non-stationary behavior

sensing channel exhibits stronger fluctuations than communication channel

larger RIS → lower spatial correlation

MLP predictions closely match theoretical curves

🔬 Reproducibility Tips

Fix random seed: rng(2024)

Increase RIS size gradually (30×30 → 100×100)

Ensure dataset normalization before training

Use sufficient samples (>1000) for stable learning

📖 Citation

If you use this code or find it helpful, please cite:

[Your Paper Citation Here]

📬 Contact

For questions or collaborations, please contact:

Author: [Your Name]
Email: [your_email]

⭐ Notes

This repository aims to bridge:

Physics-based modeling + Data-driven learning

to provide an efficient and interpretable solution for RIS-assisted V2V ISAC channel analysis.


