# Physics-Informed Graph Dynamics Engine (`pignn-mechanics-engine`)

![Python](https://img.shields.io/badge/Python-3.11+-blue?logo=python)
![PyTorch](https://img.shields.io/badge/PyTorch-GNN-EE4C2C?logo=pytorch)
![License](https://img.shields.io/badge/License-MIT-green)

A computational physics and graph neural network engine designed to simulate complex coupled particle dynamics while strictly preserving physical conservation laws (Energy & Momentum).

---

## 🔬 Physics Foundations & Theoretical Formulation

The engine models physical interactions as a graph $G = (V, E)$ where:
- Nodes $v_i \in V$ represent particles with state vectors $\mathbf{s}_i = (\mathbf{r}_i, \mathbf{v}_i, m_i, q_i)$.
- Edges $e_{ij} \in E$ represent inter-particle force vectors governed by classical potential fields:

$$V(\mathbf{r}_{ij}) = \frac{1}{2} k (\Vert{}\mathbf{r}_{ij}\Vert{} - l_0)^2 - G \frac{m_i m_j}{\Vert{}\mathbf{r}_{ij}\Vert{}}$$

### Symplectic Integration
State updates employ the Velocity-Verlet algorithm to minimize energy drift over continuous integration steps $\Delta t$:

$$\mathbf{r}_i(t + \Delta t) = \mathbf{r}_i(t) + \mathbf{v}_i(t)\Delta t + \frac{1}{2}\mathbf{a}_i(t)\Delta t^2$$
$$\mathbf{v}_i(t + \Delta t) = \mathbf{v}_i(t) + \frac{\mathbf{a}_i(t) + \mathbf{a}_i(t + \Delta t)}{2}\Delta t$$

---

## 🧪 Planned Architecture & Modules

- **`src/physics/`**: Numerical integrators (Euler, Velocity-Verlet, RK4) with energy drift monitors.
- **`src/graph/`**: Dynamic spatial graph construction and sparse edge updates.
- **`benchmarks/`**: Keplerian orbital trajectory verification and elastic mass-spring lattice models.
