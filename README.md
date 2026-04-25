## Project Overview

This project was originally intended as a foundation for simulating quantum systems on a lattice (e.g. spin models on a hexagonal/honeycomb structure). While a full simulation was not completed, the current implementation focuses on constructing the lattice geometry and defining nearest-neighbour interactions.

## Lattice Construction

The code generates a 2D hexagonal (honeycomb) lattice using two spanning vectors:

* A horizontal vector
* A 60° offset vector

A grid of points is constructed from these vectors and then split into two sublattices via a vertical offset, producing the characteristic bipartite structure used in many lattice-based quantum models.

Multiple approaches (`Attempt 1–3`) are included, showing iterative improvements in:

* Coordinate generation
* Numerical stability (tolerance handling)
* Neighbour detection

## Coupling Matrix

An interaction matrix `A` is constructed such that:

* `A(j, k)` represents the coupling between sites `j` and `k`
* Only nearest neighbours have nonzero entries
* Coupling strengths depend on bond orientation:

  * `Jx`, `Jy`, `Jz` correspond to different link directions

Neighbour detection is performed geometrically using:

* Distance thresholds
* Angle-based classification of bonds (x, y, z types)

The final version enforces (where possible):

* One x-, y-, and z-type interaction per site
* Improved floating-point tolerance handling

## Limitations

* No full quantum simulation (e.g. Hamiltonian construction or time evolution)
* Finite lattice only (no boundary condition handling)
* Neighbour detection depends on numerical tolerances
* O(N²) scaling for neighbour search (not optimized)

## Status

Work in progress. The repository currently provides:

* A working hexagonal lattice generator
* A prototype nearest-neighbour coupling matrix

but does not yet include higher-level quantum simulation functionality.
