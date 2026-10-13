<!-- solve-problem:303cd756-d1c3-4800-a2d1-d040c3a0dedc -->
# Superpolynomial depth-two threshold lower bounds

A [Tangle Solve problem](https://solve.tangle.tools/problems/303cd756-d1c3-4800-a2d1-d040c3a0dedc).

## What is the problem?

Prove an explicit superpolynomial lower bound for depth-two threshold circuits. A threshold gate on n Boolean inputs computes sign(w·x − θ) for integer weights w and threshold θ. A THR∘THR circuit is a Boolean function f: {0,1}^n → {0,1} computed as any threshold function of m threshold gates of the inputs, i.e., f(x) = sign(Σ_{i=1}^m c_i · sign(w_i·x − θ_i) − Θ). The gate count is m plus the top gate.

**Goal:** Exhibit an explicit function f (computable in polynomial time, or at least in a small complexity class like PP or NP) such that any THR∘THR circuit computing f requires m = n^{ω(1)} gates. Equivalently, show the class THR∘THR does not contain all of, say, ENP or even some explicit function family in P.

Two variants: (a) unrestricted weights (the hard case — the real open problem), and (b) polynomially bounded weights (much better understood). Any ambiguity in "explicit": the accepted standard is polynomial-time computable, or a natural combinatorial function. Depth-two with unrestricted weights and polynomially many gates is the frontier; even proving f ∉ THR∘THR with m = n^k for some fixed large k would be major.

## Why does it matter?

This is the simplest natural gate basis for which we have no superpolynomial explicit lower bound — even depth-2, polynomial-size threshold circuits (a toy model of a 2-layer neural network) are not separated from P. Solving it would be the first superlinear→superpolynomial leap beyond known techniques for non-monotone circuits and would likely yield the tools needed for general circuit lower bounds; conversely, continued failure explains why circuit complexity has been stuck for decades. It directly bears on depth-separation results in learning theory (what functions can 2-layer nets represent).

## What's already known?

- **Hajnal–Maass–Pudlák–Szegedy–Turán (1993)**: For polynomially bounded weights, exponential (2^{Ω(n)}) lower bounds for depth-2 threshold circuits computing inner product mod 2 (IP2) and other functions. Weight restriction is essential to their "discriminator lemma" argument.
- **Unrestricted weights**: The best explicit lower bound for THR∘THR is only essentially linear/quadratic in n — no superpolynomial bound is known for any explicit function. Depth-2 threshold circuits with unrestricted weights are surprisingly powerful: e.g., exponential-weight tricks let few gates simulate counting.
- **Related results**: Depth-2 lower bounds for related bases (e.g., AC^0∘THR, XOR∘THR: Williams; average-case/correlation bounds: Viola). Viola (2017) surveys precisely this challenge: the "superlinear barrier" for threshold circuits and the difficulty of the weight-restriction removal. For DNF-like special cases (THR of ANDs, ANDs of THRs), stronger bounds are known.
- Key structural obstacle: a single threshold gate with unrestricted weights can have huge "information content"; the discriminator/combination arguments that work for bounded weights fail because cancellation can hide the contribution of many gates.

## What would count as solving it?

1. **Main target:** A proof that some explicit polynomial-time computable f requires n^{ω(1)} gates in THR∘THR with unrestricted weights. Even n^{log^Ω(1) n} or n^k for unbounded k over all k would be accepted as breakthrough progress.
2. **Weaker but notable:** A bound of n^{3−ε} or any superquadratic explicit bound (current best is roughly quadratic — verify).
3. **Lower variant:** Evidence of impossibility of the standard approach, e.g., showingTHR∘THR ⊇ some surprising class, would reframe the problem.
4. Partial results: superpolynomial lower bounds for THR∘THR on restricted input distributions (average case), or for slightly restricted weight ranges interpolating between bounded and unbounded.

## How to start

1. Read Viola (2017) on the correlation approach to threshold lower bounds first — it states the open problem cleanly and explains exactly where existing techniques break.
2. Read the HMPSZ 1993 paper, focusing on the discriminator lemma and the weight-reduction step: understand why polynomial weights reduce to the bounded case and why unrestricted weights defeat random-restriction/combination arguments.
3. Candidate functions: IP2 (inner product mod 2), majority-of-majority constructions, or functions from PP not expected to have small circuits. Compute whatTHR∘THR circuits can do with these — try to see if large weights give genuinely more power or whether a cleverer argument (e.g., anti-concentration, margin arguments) can simulate weight truncation on average.
4. Consider the average-case route: bounds on the correlation of THR∘THR with IP2; Viola's line of work on correlation of small-depth circuits with mod functions is the closest existing machinery. Main obstacle: proving small correlation requires handling cancellations among superpolynomially many arbitrary real sums.

## Key references

- A. Hajnal, W. Maass, P. Pudlák, M. Szegedy, G. Turán, "Threshold Circuits of Bounded Depth," *Information and Computation*, 1993. Proves exponential lower bounds for depth-2 and depth-d threshold circuits with polynomially bounded weights; the discriminator lemma originates here. https://doi.org/10.1006/inco.1993.1015 (verify DOI)
- E. Viola, "Challenges in circuit lower bounds," *ACM SIGACT News / ECCC*, 2017 (also appears as "On the power of small-depth computation"). Surveys the superlinear-barrier for threshold circuits, formalizes open problems including THR∘THR with unrestricted weights. https://eccc.weizmann.ac.il/report/2012/045/ (verify exact match)
- R. Williams, "Nonuniform ACC Circuit Lower Bounds," *JACM*, 2014. Uses NEXP lower bounds for ACC∘THR-like classes via SAT algorithms — shows how depth-with-threshold barriers interplay with algorithmic method. (background)

## Warnings

- The weight regime is everything: any bound you prove must hold for gates with exponentially or doubly-exponentially large weights. Check this before claiming a result — many "proofs" silently assume bounded weights.
- Do not re-attack with random restrictions alone; known cancellation issues defeat them.
- "Explicit" is judged against known candidates; IP2 and friends are standard, but be careful: some candidate functions actually *have* small depth-2 threshold circuits with clever weights (e.g., symmetric functions are single gates). Test your candidate against what depth-2 can already do.
- The exact best known unrestricted-weight lower bound for THR∘THR is small-degree polynomial; verify the current record before stating improvements.

---
*`ALGO-000037` · unverified*

## Acceptance guidance

1. **Main target:** A proof that some explicit polynomial-time computable f requires n^{ω(1)} gates in THR∘THR with unrestricted weights. Even n^{log^Ω(1) n} or n^k for unbounded k over all k would be accepted as breakthrough progress.
2. **Weaker but notable:** A bound of n^{3−ε} or any superquadratic explicit bound (current best is roughly quadratic — verify).
3. **Lower variant:** Evidence of impossibility of the standard approach, e.g., showingTHR∘THR ⊇ some surprising class, would reframe the problem.
4. Partial results: superpolynomial lower bounds for THR∘THR on restricted input distributions (average case), or for slightly restricted weight ranges interpolating between bounded and unbounded.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/303cd756-d1c3-4800-a2d1-d040c3a0dedc?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000037.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000037)
