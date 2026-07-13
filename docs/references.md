# References — The Self-Evolving Platform

Annotated bibliography for [`paper.md`](./paper.md). Every link was verified to resolve at time of writing (2026-07-13). Where a canonical DOI and an open-access mirror both exist, both are listed. arXiv `abs` pages are preferred as stable landing pages.

Grade legend (relevance to the thesis): **[FND]** foundational mechanism · **[SI]** self-improving agents · **[SA]** self-adaptive/autonomic · **[APR]** program repair · **[RE]** requirements engineering · **[EVAL]** evaluation/ontology · **[LLMGEN]** the platform under study.

---

## Primary basis

**[1] Agaev, R. (2026). "Beyond SWE-bench: Benchmarking AI-Driven Platform Engineering at SDLC Scale."** [LLMGEN, EVAL]
Establishes the 5-level benchmark scope hierarchy (Level 5 = platform engineering) and the measured LLMGen deployment (44 features, ~6.8M LOC, 117 days, composite 94/100). The empirical basis for "Level-5 platform generation."
- Repo: https://github.com/romanagaev/llmgen-benchmark
- Medium: https://medium.com/@romanagaev/i-benchmarked-my-ai-engineering-platform-against-swe-bench-1b98b1592cc2
- Dev.to: https://dev.to/romanagaev/i-built-an-ai-platform-that-delivers-333-loc-per-dollar-heres-how-i-benchmarked-it-1oao

**[2] Agaev, R. (2026). "LLMGen Tier 3 — Native AI IDE (VS Code Fork)."** [LLMGEN]
LLMGen program documentation (`docs/tier3-llmgen-ide/` in the LLMGen program repository — **not included in this repo**): feasibility, architecture, and execution plan for a self-hosting LLMGen IDE produced by LLMGen's own Brownfield → Addon workflow, including the governance controls (human gates, four-tier verification, immutable CMS, signed staged self-update) relied on in Section 5.4.

---

## Foundational: self-referential / recursive self-improvement

**[5] Schmidhuber, J. (2003). "Gödel Machines: Self-Referential Universal Problem Solvers Making Provably Optimal Self-Improvements."** [FND]
The theoretical anchor: a system that rewrites its own code only when it can *prove* the rewrite is beneficial. Optimal but practically unattainable; motivates empirical substitutes.
- arXiv: https://arxiv.org/abs/cs/0309048
- Author page (v4, HTML): https://people.idsia.ch/~juergen/gmweb4/gmweb4.html

**[19] Bostrom, N. (2014). *Superintelligence: Paths, Dangers, Strategies*. Oxford University Press. ISBN 978-0199678112.** [FND]
Frames recursive self-improvement ("intelligence explosion") and its safety/control stakes; motivates the governance emphasis (Section 9).
- Overview & bibliographic record: https://en.wikipedia.org/wiki/Superintelligence:_Paths,_Dangers,_Strategies
- Publisher record: https://global.oup.com/academic/product/superintelligence-9780199678112 (may require JavaScript)

---

## Self-improving agents (agent-scope, benchmark-objective)

**[6] Zhang, J., Hu, S., Lu, C., Lange, R., Clune, J. (2025). "Darwin Gödel Machine: Open-Ended Evolution of Self-Improving Agents."** [SI]
A self-referential coding agent that edits its own codebase over an archive; SWE-bench 20.0→50.0%, Polyglot 14.2→30.7%. Explicitly discusses objective-hacking, cost (~$22K / 2 weeks per 80-iteration run), and safety.
- arXiv: https://arxiv.org/abs/2505.22954
- Project: https://sakana.ai/dgm/ · Code: https://github.com/jennyzzt/dgm

**[7] Yin, X., Wang, X., Pan, L., Lin, L., Wan, X., Wang, W. Y. (2024/2025). "Gödel Agent: A Self-Referential Agent Framework for Recursive Self-Improvement." ACL 2025.** [SI]
Runtime self-modification of an agent's own logic via monkey-patching, guided only by high-level objectives.
- arXiv: https://arxiv.org/abs/2410.04444 · Code: https://github.com/Arvid-pku/Godel_Agent

**[8] Zelikman, E., Lorch, E., Mackey, L., Kalai, A. T. (2023). "Self-Taught Optimizer (STOP): Recursively Self-Improving Code Generation."** [SI]
A language-model-infused "improver" improves itself; notes it is *not* full RSI (weights unchanged) and measures sandbox-bypass frequency — an early, explicit safety signal.
- arXiv: https://arxiv.org/abs/2310.02304 · Code: https://github.com/microsoft/stop

**[9] Robeyns, M., Aitchison, M., Szpruch, L. (2025). "A Self-Improving Coding Agent (SICA)."** [SI]
Eliminates the meta-agent/target-agent split; edits its entire Python codebase; 17→53% on a SWE-bench Verified subset with safety/resource constraints.
- arXiv: https://arxiv.org/abs/2504.15228 · Code: https://github.com/MaximeRobeyns/self_improving_coding_agent

**[10] Hu, S., Lu, C., Clune, J. (2024/2025). "Automated Design of Agentic Systems (ADAS)." ICLR 2025.** [SI]
A fixed meta-agent programs ever-better agents in code into a growing archive (Meta Agent Search). Optimizer and optimized are distinct — contrast with C4/self-reference.
- arXiv: https://arxiv.org/abs/2408.08435 · Code: https://github.com/ShengranHu/ADAS

**[11] Google DeepMind (2025). "AlphaEvolve: A Coding Agent for Scientific and Algorithmic Discovery."** [SI]
Evolves whole codebases against automated evaluators; improved data-center scheduling and a component of its own training stack; found a 4×4 complex matrix-mult algorithm (48 mults) improving on Strassen after 56 years.
- arXiv: https://arxiv.org/abs/2506.13131
- Blog: https://deepmind.google/blog/alphaevolve-a-gemini-powered-coding-agent-for-designing-advanced-algorithms/

**[20] Y. Wang et al. (2025). "Huxley-Gödel Machine: Human-Level Coding Agent Development by an Approximation of the Optimal Self-Improving Machine."** [SI]
Approximates Gödel-Machine-style selection via clade-metaproductivity; identifies the "metaproductivity–performance mismatch" in greedy self-improvers — relevant to SE-6 (avoiding objective-hacking drift).
- arXiv: https://arxiv.org/abs/2510.21614

## Within-task self-improvement primitives

**[12] Shinn, N., Cassano, F., Berman, E., Gopinath, A., Narasimhan, K., Yao, S. (2023). "Reflexion: Language Agents with Verbal Reinforcement Learning." NeurIPS 2023.** [SI]
Verbal self-reflection stored in episodic memory; 91% pass@1 on HumanEval. A Sense/Specify primitive.
- arXiv: https://arxiv.org/abs/2303.11366 · Code: https://github.com/noahshinn024/reflexion

**[13] Madaan, A. et al. (2023). "Self-Refine: Iterative Refinement with Self-Feedback." NeurIPS 2023.** [SI]
Single-model generate→feedback→refine loop; ~20% average improvement without training. The Synthesize-phase refinement primitive.
- arXiv: https://arxiv.org/abs/2303.17651 · Project: https://selfrefine.info/

**[14] Wang, G. et al. (2023). "Voyager: An Open-Ended Embodied Agent with Large Language Models."** [SI]
Lifelong learning via an ever-growing, retrievable **skill library** of executable code — the capability-accumulation analog for a self-evolving platform.
- arXiv: https://arxiv.org/abs/2305.16291 · Project: https://voyager.minedojo.org/

---

## Self-managing software: autonomic computing & self-adaptive systems

**[3] Kephart, J. O., Chess, D. M. (2003). "The Vision of Autonomic Computing." *IEEE Computer* 36(1):41–50.** [SA, FND]
Introduces the **MAPE-K** loop (Monitor–Analyze–Plan–Execute over Knowledge); the control-loop template generalized by SEL (Section 5.1).
- DOI: https://doi.org/10.1109/MC.2003.1160055
- Open PDF: https://www.cs.cmu.edu/~15849g/readings/kephart03.pdf

**[4] de Lemos, R., Giese, H., Müller, H. A., Shaw, M., et al. (2013). "Software Engineering for Self-Adaptive Systems: A Second Research Roadmap." LNCS 7475, Springer.** [SA]
Design space, processes, decentralization, and run-time V&V for self-adaptive systems; grounds the "adaptation within a pre-designed space" limitation (Section 2.2).
- DOI: https://doi.org/10.1007/978-3-642-35813-5_1
- Open PDF: https://software.imdea.org/~alessandra.gorla/papers/deLemos-Roadmap-SEfSAS213.pdf

---

## Program repair & requirements from defects/text

**[15] Jimenez, C. E., Yang, J., Wettig, A., Yao, S., Pei, K., Press, O., Narasimhan, K. (2024). "SWE-bench: Can Language Models Resolve Real-World GitHub Issues?" ICLR 2024.** [APR, EVAL]
The canonical issue→patch benchmark; the Level-2 reference point and the defect-derived-requirement precedent.
- arXiv: https://arxiv.org/abs/2310.06770 · Code: https://github.com/SWE-bench/SWE-bench

**[16] Monperrus, M. (2018). "Automatic Software Repair: A Bibliography." *ACM Computing Surveys* 51(1).** [APR]
Structured survey of bug oracles (tests, contracts, crashing inputs) and repair operators; the mechanism behind "requirements assessed from bugs and misfunction." See also the continuously updated Living Review.
- DOI: https://doi.org/10.1145/3105906
- Living Review (PDF): https://hal.science/hal-01956501v6/file/repair-living-review.pdf

**[17] Mavin, A., Wilkinson, P., Harwood, A., Novak, M. (2009). "Easy Approach to Requirements Syntax (EARS)." 17th IEEE International Requirements Engineering Conference (RE '09).** [RE]
Five natural-language requirement patterns (ubiquitous, event-driven, state-driven, optional-feature, unwanted-behavior). The structured external-intake grammar (Section 5.2).
- DOI: https://doi.org/10.1109/RE.2009.9
- Official guide: https://alistairmavin.com/ears/

---

## Evaluation / ontology framing

**[18] Morris, M. R., Sohl-Dickstein, J., Fiedel, N., Warkentin, T., Dafoe, A., Faust, A., Farabet, C., Legg, S. (2024). "Levels of AGI for Operationalizing Progress on the Path to AGI." ICML 2024.** [EVAL]
Capability/generality/autonomy levels analogous to SAE driving automation; the template for the Levels of Self-Evolution ontology (Section 4).
- arXiv: https://arxiv.org/abs/2311.02462
- DeepMind: https://deepmind.google/research/publications/66938/

---

*Link-verification note:* arXiv `abs/` and publisher `doi.org/` links are stable identifiers. Blog/project mirrors (Sakana, DeepMind, selfrefine.info, alistairmavin.com, voyager.minedojo.org) are supplementary and may change; the arXiv/DOI entry is authoritative in each case.
