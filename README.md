# Dataset for FMO-QVM-HCI-HSQD Quantum Simulations

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC--BY--4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Zenodo](https://img.shields.io/badge/Zenodo-23909476-blue.svg)](https://zenodo.org/records/23909476)
[![arXiv](https://img.shields.io/badge/arXiv-2610.41986-b31b1b.svg)](https://doi.org/10.48550/arXiv.2610.41986)

## Zenodo

- **Record:** https://zenodo.org/records/23909476

## Overview
This repository contains the input files, raw quantum-hardware measurement data and plotted data supporting the results presented in:

**"Resource efficient Sample Based Quantum Simulation through Fragmentation and Virtual Partitioning of QPU"**
arXiv:2610.41986, https://doi.org/10.48550/arXiv.2610.41986

The work combines the two-body fragment molecular orbital method (FMO2) with sample-based quantum diagonalization. Fragment Hamiltonians are solved with sample-based quantum diagonalization (SQD) or with half-qubit heat-bath configuration interaction sample-based quantum diagonalization (HCI-HSQD). Fragment circuits are executed either sequentially or in parallel within a quantum virtual machine (QVM) on IBM quantum processors.

The datasets include:
- Water trimer, STO-3G: four methods on `ibm_marrakesh`
- Carmofur bound to SARS-CoV-2 Mpro, STO-3G: two QVM methods on `ibm_marrakesh`, and the classical and quantum seed comparison


---

## Authors
- R. Pradeep
- Anurag Chaudhary
- Ashish Kumar Patra
- Anurag K.S.V.
- Ruchika Bhat
- Sai Shankar P.
- G. Jaiganesh

**Affiliation:** Qclairvoyance Quantum Labs Pvt. Ltd.

---

## Dataset Structure

### Water trimer, STO-3G
`data/water_sto3g/`

- Full orbital space: monomers (10e,7o), dimers (20e,14o)
- `ibm_marrakesh`, 10,000 shots per fragment, transpiler optimization level 3
- Methods: FMO-SQD, FMO-QVM-SQD, FMO-HCI-HSQD, FMO-QVM-HCI-HSQD
- Reference: FMO-FCI

### Carmofur-Mpro, STO-3G
`data/carmofur_sto3g/`

- 55-atom cavity: Ser144, Cys145, Gly146 and the covalently bound hexylcarbamoyl tail
- Active spaces: monomers (8e,8o), dimers (16e,16o)
- `ibm_marrakesh`, 10,000 shots per fragment, one batched QVM job per method
- Methods: FMO-QVM-SQD, FMO-QVM-HCI-HSQD
- Reference: FMO-CASCI
- Also contains the data for the classical and quantum seed comparison on dimer 1-3



Each system folder contains:
- `*.inp` — OpenFMO input (geometry, fragmentation, active space)
- `*.xyz` — geometry used in the calculations
- `bitstrings_<method>.csv` — all measured bitstrings and their counts
- `plotted_data.txt` — all values shown in the figures, the computational settings and the IBM job identifiers

---

## File Formats and Conventions
- Bitstring files are CSV with columns `method, fragment, qubits, bitstring, count`.
- Fragment labels: water molecules 0, 1, 2. Carmofur: 0 Ser144, 1 Cys145, 2 Gly146, 3 ligand. Dimers are labelled by their two monomers, for example `1-3`.
- Bitstrings follow the Qiskit ordering: the rightmost bit is qubit 0 and active orbital 0.
- SQD bitstrings contain both spin sectors, with the beta string on the left and the alpha string on the right.
- HCI-HSQD bitstrings encode a single spin string.

---

## Reproducibility
The datasets provided here are sufficient to reproduce all plots and numerical results reported in the paper.

The simulation code is proprietary and not publicly available.

---

## Software Availability
The workflow code used to generate the fragment Hamiltonians, construct and execute the quantum circuits, run the QVM batch execution and post-process the measurements is proprietary to Qclairvoyance Quantum Labs Pvt. Ltd. and is not publicly available.

The calculations make use of the following publicly available software:
- OpenFMO (fragment molecular orbital calculations)
- FragIt (fragmentation)
- PySCF (CASCI, CISD and CCSD(T) reference calculations)
- Qiskit and qiskit-addon-sqd (circuit construction, transpilation and SQD)
- ffsim (LUCJ ansatz)
- Dice (semistochastic heat-bath configuration interaction)

---

## Units
- Energy: Hartree (deviations in millihartree)
- Distance: Å
- QPU time: seconds (IBM-reported quantum execution time)

---

## License
This dataset is licensed under the Creative Commons Attribution 4.0 International (CC-BY 4.0).

---

## Citation
If you use this dataset, please cite the article and the dataset:

R. Pradeep, Anurag Chaudhary, Ashish Kumar Patra, Anurag K.S.V., Ruchika Bhat, Sai Shankar P., G. Jaiganesh (2026).
*Resource efficient Sample Based Quantum Simulation through Fragmentation and Virtual Partitioning of QPU*.
arXiv:2610.41986. https://doi.org/10.48550/arXiv.2610.41986

Dataset: Zenodo, https://zenodo.org/records/23909476
