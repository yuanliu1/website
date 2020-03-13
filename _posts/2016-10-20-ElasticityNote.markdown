---
layout: post
title: Miscellaneous notes on linear elasticity
date: 2016-10-20 18:00
description: research note
---


### Tensor
Some good introductions to tensors can be found in
- Javier Bonet and Richard D. Wood, Nonlinear Continuum Mechanics for Finite Element Analysis, Chapter 2 
- Piaras Kelly, [Mechanics Lecture Notes Part III: Foundations of Continuum Mechanics](http://homepages.engineering.auckland.ac.nz/~pkel015/SolidMechanicsBooks/Part_III/index.html)

### Principle of virtual work
For a static, linear elastic boundary value problem, the governing equation reads

$$
\nabla \cdot \boldsymbol{\sigma} + \boldsymbol{b} = \boldsymbol{o}, \quad \text{in} \quad \Omega
$$


<!-- $$$
\begin{align}
  \nabla \cdot \boldsymbol{\sigma} + \boldsymbol{b} = \boldsymbol{o}, \quad \text{in} \quad \Omega
  \label{eq:equilbrium}
\end{align} 
$$$
 -->
with the boundary conditions

$$
\begin{align}
  \boldsymbol{u} &= \boldsymbol{u}^*, \quad \text{on} \quad \Gamma_u, \\
  \boldsymbol{\sigma} \cdot \boldsymbol{n} &= \boldsymbol{t}^*, \quad \text{on} \quad \Gamma_s. 
  \label{eq:BC}
\end{align}
$$

Consider a virtual displacement filed $$\delta\boldsymbol{u}$$ which satisfies $$\delta\boldsymbol{u} = \boldsymbol{o}$$ on $$\Gamma_u$$. Multiply $$\delta\boldsymbol{u}$$ on both side of \eqref{eq:equilbrium} and integrate over $$\Omega$$, we obtain


$$
\begin{align}
  & \int_{\Omega} (\nabla \cdot \boldsymbol{\sigma}) \cdot \delta\boldsymbol{u} \, dV + \int_{\Omega} \boldsymbol{b} \cdot \delta\boldsymbol{u} \, dV \\
  &= \int_{\Omega} \nabla \cdot (\boldsymbol{\sigma} \cdot \delta\boldsymbol{u}) \, dV - \int_{\Omega} \boldsymbol{\sigma}:\nabla \delta \boldsymbol{u} \, dV + \int_{\Omega} \boldsymbol{b} \cdot \delta\boldsymbol{u} \, dV \\
  &= \int_{\Gamma} \boldsymbol{n} \cdot (\boldsymbol{\sigma} \cdot \delta\boldsymbol{u}) \, dS - \int_{\Omega} \boldsymbol{\sigma}:\nabla\delta\boldsymbol{u} \, dV + \int_{\Omega} \boldsymbol{b} \cdot \delta\boldsymbol{u} \, dV \\
  &= \int_{\Gamma_s} \boldsymbol{t}^* \cdot \delta\boldsymbol{u} \, dS - \int_{\Omega} \boldsymbol{\sigma}:\nabla\delta\boldsymbol{u} \, dV + \int_{\Omega} \boldsymbol{b} \cdot \delta\boldsymbol{u} \, dV \\
  &= 0,
  \label{eq:virtualwork}
\end{align} 
$$

which can be rewrite as

$$
\begin{align}
  \int_{\Omega} \boldsymbol{\sigma}:\nabla\delta\boldsymbol{u} \, dV &= \int_{\Gamma_s} \boldsymbol{t}^* \cdot \delta\boldsymbol{u} \, dS + \int_{\Omega} \boldsymbol{b} \cdot \delta\boldsymbol{u}\, dV,
  \label{eq:virtualwork1}
\end{align} 
$$

or

$$
\begin{align}
  \int_{\Omega} \boldsymbol{\sigma}:\delta\boldsymbol{\epsilon} \, dV &= \int_{\Gamma_s} \boldsymbol{t}^* \cdot \delta\boldsymbol{u} \, dS + \int_{\Omega} \boldsymbol{b} \cdot \delta\boldsymbol{u}\, dV.
  \label{eq:virtualwork2}
\end{align} 
$$

In arriving \eqref{eq:virtualwork} we invoked the Green's theorem, and in arriving \eqref{eq:virtualwork2} from \eqref{eq:virtualwork1}, we used the property that $\boldsymbol{\sigma}$ is symmetric and $\boldsymbol{\sigma}:\nabla\delta\boldsymbol{u}$ = $\boldsymbol{\sigma}:(\text{sym}(\nabla\delta\boldsymbol{u}) + \text{skewsym}(\nabla\delta\boldsymbol{u}))$ = $\boldsymbol{\sigma}:\text{sym}(\nabla\delta\boldsymbol{u})$ = $\boldsymbol{\sigma}:\delta\boldsymbol{\epsilon}$.

The \eqref{eq:virtualwork2} has clear physical meaning, that is, the internal work stored in the solid (LHS) is equal to the external work done by the surface traction and body force (RHS).

### Constitutive relation for istropic solid
The constitutive relation, or the stress--strain ($\boldsymbol{\sigma}--\boldsymbol{\epsilon}$) relation, for the istropic solid is

$$
\begin{align}
  \boldsymbol{\sigma} = \boldsymbol{C} : \boldsymbol{\epsilon},
\end{align}
$$

where $C_{ijkl} = \lambda \delta_{ij} \delta_{kl} + \mu (\delta_{ik} \delta_{jl} + \delta_{il} \delta_{jk})$. In index from,
$$
\begin{align}
  \sigma_{ij} = 2\mu\epsilon_{ij} + \lambda \epsilon_{kk} \delta_{ij}.
\end{align}
$$

### Betti reciprocal theorem
Consider two different equilibrium states of a solid $\boldsymbol{u}^{(1)}$, $\boldsymbol{\epsilon}^{(1)}$, $\boldsymbol{\sigma}^{(1)}$ and $\boldsymbol{u}^{(2)}$, $\boldsymbol{\epsilon}^{(2)}$, $\boldsymbol{\sigma}^{(2)}$. The two states could be under different boundary conditions. We can show that 

$$
\begin{align}
  & \int_{\Gamma} (\boldsymbol{n} \cdot \boldsymbol{\sigma}^{(1)}) \cdot \boldsymbol{u}^{(2)} \, dS + \int_{\Omega} \boldsymbol{b}^{(1)} \cdot \boldsymbol{u}^{(2)} \, dV \\
  &= \int_{\Gamma} (\boldsymbol{n} \cdot \boldsymbol{\sigma}^{(2)}) \cdot \boldsymbol{u}^{(1)} \, dS + \int_{\Omega} \boldsymbol{b}^{(2)} \cdot \boldsymbol{u}^{(1)} \, dV \\
  &= \int_{\Omega} \boldsymbol{\sigma}^{(1)}:\boldsymbol{\epsilon}^{(2)} \, dV \\
  &= \int_{\Omega} \boldsymbol{\sigma}^{(2)}:\boldsymbol{\epsilon}^{(1)} \, dV.
\end{align}
$$

To prove it, first observe that $\boldsymbol{\sigma}^{(1)}:\boldsymbol{\epsilon}^{(2)}$ = $\boldsymbol{\epsilon}^{(2)}:\boldsymbol{C}:\boldsymbol{\epsilon}^{(1)}$ = $\boldsymbol{\epsilon}^{(1)}:\boldsymbol{C}:\boldsymbol{\epsilon}^{(2)}$ = $\boldsymbol{\sigma}^{(2)}:\boldsymbol{\epsilon}^{(1)}$.
Then note that
$$
\begin{align}
  & \int_{\Gamma} (\boldsymbol{n} \cdot \boldsymbol{\sigma}^{(1)}) \cdot \boldsymbol{u}^{(2)} \, dS + \int_{\Omega} \boldsymbol{b}^{(1)} \cdot \boldsymbol{u}^{(2)} \, dV \\
  &= \int_{\Omega} \nabla \cdot (\boldsymbol{\sigma}^{(1)} \cdot \boldsymbol{u}^{(2)}) \, dV + \int_{\Omega} \boldsymbol{b}^{(1)} \cdot \boldsymbol{u}^{(2)} \, dV \\
  &= \int_{\Omega} (\nabla \cdot \boldsymbol{\sigma}^{(1)} + \boldsymbol{b}^{(1)}) \, dV + \int_{\Omega} \boldsymbol{\sigma}^{(1)} : \nabla\boldsymbol{u}^{(2)} \, dV \\
  &= \int_{\Omega} \boldsymbol{\sigma}^{(1)} : \boldsymbol{\epsilon}^{(2)} \, dV.
\end{align}
$$
Similarly, we have
$$
\begin{align}
  & \int_{\Gamma} (\boldsymbol{n} \cdot \boldsymbol{\sigma}^{(2)}) \cdot \boldsymbol{u}^{(1)} \, dS + \int_{\Omega} \boldsymbol{b}^{(2)} \cdot \boldsymbol{u}^{(1)} \, dV \\
  &= \int_{\Omega} \boldsymbol{\sigma}^{(2)} : \boldsymbol{\epsilon}^{(1)} \, dV.
\end{align}
$$
This completes the proof of the Betti reciprocal theorem.


### Linear elasticity
[Relations between elastic constants]({{ site.baseurl }}/assets/pdf/LinearElasticHandout.pdf)

### Curvilinear coordinates
[Linear elastic equations in curvilinear coordinates]({{ site.baseurl }}/assets/pdf/CurvilinearHandout.pdf)
