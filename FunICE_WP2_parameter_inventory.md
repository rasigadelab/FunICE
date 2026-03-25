# WP2 Parameter Inventory for the pP36 Biofilm-Scale Model

This companion file lists the main parameter families used in WP2. It is designed to sit outside the main proposal text so that the modelling strategy remains readable in the grant while the technical inventory stays versionable and easy to update.

Not all parameters below will be estimated simultaneously in the final calibrated model. In line with the feasibility strategy described in WP2, the default validated model will be the reduced biofilm model, and additional layers or explicit copy number dynamics will only be retained if supported by WP1 data and posterior predictive checks. Parameters not directly observed in WP1 will be treated as assumed scenario parameters and propagated through structured sensitivity analyses before biological interpretation.

## Parameter status labels

| Status | Meaning |
| --- | --- |
| Assumed | Fixed from model design, experimental setup, or sensitivity analysis. |
| Measured | Directly estimated from WP1 experiments, possibly with uncertainty bounds. |
| Model-defined | Chosen as part of the model structure and then constrained by WP1 observables. |
| Inferred | Estimated by calibration of the stochastic model against WP1 data. |

## 1. Ecological context

| Entity | Process | Parameter | Role in the model | Status | Task |
| --- | --- | --- | --- | --- | --- |
| Biofilm | Spatial layout | Biofilm geometry / neighborhood graph | Defines which cells can interact locally and how space is represented in the biofilm-scale model | Assumed | T2.2 |
| Biofilm | Crowding | Local carrying capacity | Limits local bacterial density and growth through crowding or shared resources | Assumed | T2.2 |
| Biofilm | Diffusion | Nutrient field parameters | Control how nutrient availability varies across the biofilm; treated as assumed ecological parameters unless direct measurements become available | Assumed | T2.2 |
| Biofilm | Diffusion | Antibiotic field parameters | Control local antibiotic exposure and its spatial or temporal gradients; calibrated only when WP1 provides direct constraints, otherwise varied by sensitivity analysis | Assumed / measured | T2.2 |
| Treatment regime | Stress schedule | Stress regime class | Encodes constant, sublethal, pulsed, or patch-specific exposure scenarios | Assumed | T2.2, T2.3 |
| Metapopulation | Connectivity | Patch connectivity / migration rate | Captures movement between patches in the optional metapopulation extension and is only activated after validation of the core biofilm model | Assumed | T2.2 |

## 2. Host background and host physiology

| Entity | Process | Parameter | Role in the model | Status | Task |
| --- | --- | --- | --- | --- | --- |
| Bacterial cell | Identity | Host background class | Represents the *Legionella* lineage or isolate category used in WP1 | Measured | T2.1, T2.2 |
| Bacterial cell | Growth | Baseline growth rate | Growth rate of the host in the absence of pP36 state-specific effects | Measured / inferred | T2.1 |
| Bacterial cell | Death | Basal death rate | Baseline death rate in the absence of antibiotic-induced killing | Inferred | T2.1 |
| Bacterial cell | Antibiotic response | Growth-killing coupling factor | Governs how antibiotic killing depends on effective growth | Inferred | T2.1 |
| Bacterial cell | Permissiveness | Recipient permissiveness class | Encodes whether a host background is permissive, weakly permissive, or non-permissive for pP36 | Measured / inferred | T2.2 |
| Bacterial cell | Genomic context | Insertion-context class | Distinguishes hosts with canonical insertion site, altered context, or no insertion site | Measured | T2.2 |

## 3. Coarse-grained intracellular pP36 state model

| Entity | Process | Parameter | Role in the model | Status | Task |
| --- | --- | --- | --- | --- | --- |
| pP36 | State definition | State set | Discrete intracellular states retained in the reduced model, e.g. integrated, excised/low-copy, excised/high-copy | Model-defined | T2.1 |
| pP36 | State transitions | Transition rates | Rates of excision, reintegration, and effective state switching between coarse-grained states | Inferred | T2.1 |
| pP36 | Host effect | Host-growth modifier per state | State-dependent effect of pP36 on host growth, potentially host-background-specific | Inferred | T2.1 |
| pP36 | Antibiotic response | State-dependent susceptibility modifier | Optional state-specific contribution to antibiotic tolerance beyond growth dependence | Inferred | T2.1 |
| pP36 | Transfer | Local conjugation rate | Effective local transfer rate between donor and recipient cells in the biofilm, inferred only when supported by direct WP1 transfer readouts | Inferred | T2.2 |
| pP36 | After transfer | Post-transfer establishment parameters | Describe maintenance, delayed activation, early loss, or persistence after transfer; reduced to a smaller host-class formulation if the data are insufficient | Inferred | T2.2 |
| pP36 | Transfer proxy | Representative copy number per state | Links discrete states to approximate dosage when transfer depends on pP36 abundance | Inferred | T2.2 |

## 4. Optional explicit copy number extension

| Entity | Process | Parameter | Role in the model | Status | Task |
| --- | --- | --- | --- | --- | --- |
| pP36 | Excision | Excision rate per integrated copy | Rate at which an integrated copy becomes excised | Inferred | T2.1 |
| pP36 | Reintegration | Reintegration rate per free copy | Rate at which an excised copy reintegrates into the chromosome | Inferred | T2.1 |
| pP36 | Replication | Autonomous replication rate per free copy | Rate of stochastic replication of excised pP36 copies | Inferred | T2.1 |
| pP36 | Loss | Loss / segregation rate per free copy | Rate at which excised copies are lost during cell growth or division | Inferred | T2.1 |
| pP36 | Host effect | Additive growth cost per copy | Explicit dosage-dependent burden imposed by free or integrated copies | Inferred | T2.1 |
| pP36 | Transfer | Copy-number-dependent transfer modifier | Optional modulation of conjugation by intracellular pP36 abundance | Inferred | T2.2 |

## 5. Calibration observables linked to WP1

| Observable family | Examples used in calibration or validation | Main task |
| --- | --- | --- |
| Single-cell state observables | parS/ParB imaging, TIMER trajectories, excision frequencies, state residence times | T2.1 |
| Molecular observables | qPCR estimates of excision and replication, transfer readouts, post-transfer persistence | T2.1, T2.2 |
| Survival observables | Time-kill curves, persistence frequencies, biphasic versus monophasic killing profiles | T2.1, T2.3 |
| Spatial observables | High-resolution biofilm imaging, local distribution of donors, recipients, and persistent subpopulations; mixed-host competitor-biofilm assay if implemented | T2.2, T2.3 |

## Practical note

The final validated version of WP2 is expected to retain:

- a reduced number of host background classes,
- a reduced number of stress-regime classes,
- the coarse-grained intracellular state model as the default predictive core,
- the metapopulation extension only after validation of the core biofilm-scale model.

In practical terms, this means that nutrient fields, antibiotic penetration profiles, and patch-connectivity assumptions will not be claimed as directly inferred unless the corresponding data are available. By default, they will be explored as scenario parameters, and only predictions robust across the tested ranges will be advanced as biological conclusions.
