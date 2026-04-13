# Prompt

Can you explain how physical symmetries are defined only at certain scales and how this relates to the re-normalization group as well as order parameters?

when I say physical symmetries are defined at a certain scale I mean: if you have a symmetric object and you describe it on an atomic scale, then the position of each atom in it is not invariant to rotations from O(3), whereas if you only describe it on a coarser scale (like you only care about the electric field lines coming from it or only care that it is macroscopically a sphere) then it is, so the question of whether or not O(3) transformations are physical symmetris of this object depends on the scale.

another example, certain thermal fluctuations are only noticeable when you describe the object from a very microscopic scale and they are all still collapsed into one macrostate. therefore, if you were to permute the system between some of these states, some of these permutations would be physical symmetries of the system on the scale of the macrostate, but not on the microscopic scale.

can you also explain how the order parameter relates to the correlation range of a system and how that relates to the energy scale we are working on?

another thing that Im getting at is that when we say that a system maximizes its entropy in thermal equilibrium, we only mean that it maximizes its entropy up to the energy constraints of the system. the highest possible entropy is one where you have a homogenous "ocean" of quarks and leptons, but that is not what we mean. 2 points on this. first, this manifests in the math by the model (scale) we use to characterize microstates. second, the reason that we do not need expect the system to come to equilibrium at the planck scale, but we do at some coarser scale (for example) is that there is not enough energy in the system to overcome the binding energy of the atoms involved. this means that we are expecting the atoms to maintain their form and hold a lower entropy form, even if the macroscopic objects that they constitute are coming to a more macroscopic thermal equilibrium. can we generalize/formalize this idea with order parameters and landau theory or something from RG flow theory? like for example, we define an order parameter such that we allow the system to maintain low entropy micro structures at some energy scale and still reach thermal equilibrium at a higher scale?

i know there are a lot of questions here, please try to address them all clearly

# Notes

### Scale-Dependent Symmetries

## 1. Scale-Dependent Symmetries

A symmetry is only meaningful relative to the **resolution** at which you describe a system. Formally, we describe a system at scale $\Lambda$ (a momentum cutoff, or equivalently a length cutoff $\ell \sim 1/\Lambda$) by a set of degrees of freedom and an **effective action** $S_\Lambda[\phi]$. The symmetry group of the system at scale $\Lambda$ is the group of transformations that leave $S_\Lambda$ invariant — and this group can genuinely change as $\Lambda$ changes. It is not fixed.

**Example:** A macroscopic sphere is O(3)-symmetric at the macroscale. At the atomic scale, the atoms sit at specific lattice positions — these are manifestly not O(3)-invariant. The symmetry *emerges* upon coarse-graining, because the atomic-scale anisotropy is an irrelevant perturbation that flows to zero under RG. The emergent symmetry at the macroscale is not an accident — it is a consequence of the RG flow washing out irrelevant structure.

---

## 2. The Renormalization Group

The RG tracks how $S_\Lambda$ changes as you lower $\Lambda$ (coarse-grain). Split the field into slow (IR) and fast (UV) modes at cutoff $\Lambda/b$ for $b > 1$:

$$\phi(k) = \phi_<(k) + \phi_>(k)$$

and integrate out the fast modes exactly:

$$e^{-S_{\Lambda/b}[\phi_<]} = \int \mathcal{D}\phi_> \, e^{-S_\Lambda[\phi_< + \phi_>]}$$

then rescale $k \to bk$, $\phi_< \to b^{-\Delta_\phi}\phi_<$ to restore the cutoff. Iterating generates the **RG flow** in the space of all possible actions. The most general action consistent with symmetry group $G$ is:

$$S[\phi] = \sum_i g_i \mathcal{O}_i[\phi]$$

Under one RG step $b = e^{d\ell}$, the couplings flow according to **beta functions**:

$$\frac{dg_i}{d\ell} = \beta_i(g_1, g_2, \ldots)$$

Operators are classified by their scaling dimension $y_i$ (where $g_i \sim b^{y_i}$):

- $y_i > 0$: **relevant** — grows under coarse-graining, dominates IR physics
- $y_i < 0$: **irrelevant** — shrinks, washes out at large scales
- $y_i = 0$: **marginal** — requires higher-order analysis

**Fixed points** $\beta_i(g^*) = 0$ for all $i$ are scale-invariant theories. The universality of critical phenomena — the fact that wildly different microscopic systems behave identically near phase transitions — follows from many different microscopic actions flowing to the same fixed point. **Irrelevant operators correspond exactly to the microscopic symmetry-breaking details that disappear upon coarse-graining.** Whether a symmetry-breaking term is irrelevant at the IR fixed point is a nontrivial dynamical statement — it can fail, in which case the microscopic symmetry-breaking survives to low energies.

The full RG flow from UV to IR takes the form:

$$S_{\Lambda_0}[\phi] \xrightarrow{\text{RG flow}} S^*[\phi] + \sum_i c_i \mathcal{O}_i^\text{relevant}$$

where $S^*$ is the fixed point action (the universality class) and the relevant operators are small perturbations away from criticality (e.g. $r \sim T - T_c$, external field $h$). The **critical exponents** are determined entirely by the eigenvalues $\{y_i\}$ of the linearized RG flow around the fixed point — which is why they are universal.

---

## 3. The Ginzburg-Landau Functional

The Ginzburg-Landau functional is the most general action for a field $\phi$ near a phase transition, consistent with symmetry group $G$, keeping only relevant and marginal operators:

$$S_\text{GL}[\phi] = \int d^dx \left[ \frac{1}{2}(\nabla\phi)^2 + \frac{r}{2}\phi^2 + \frac{u}{4!}\phi^4 + \ldots \right]$$

This is not a phenomenological guess — it is the **inevitable form** of the effective action after integrating out all UV modes, because all higher-order terms ($\phi^6$, $(\nabla^2\phi)^2$, etc.) are irrelevant and have flowed to zero. The specific coefficients $r, u, \ldots$ encode the microscopic physics; the form is universal.

---

## 4. Order Parameters and Correlation Length

The **order parameter** $\phi$ is zero in the disordered phase and nonzero in the ordered (symmetry-broken) phase. Associated to it is the correlation function:

$$G(r) = \langle \phi(x)\phi(x+r) \rangle - \langle \phi \rangle^2 \sim e^{-r/\xi}$$

where $\xi$ is the **correlation length** — the scale over which the system is self-correlated. The relation to energy scale is:

$$\xi \sim \frac{1}{m}$$

where $m$ is the mass (energy gap) of the lowest fluctuation mode of $\phi$. In the Ginzburg-Landau theory, $m^2 = r \sim (T - T_c)$, giving the mean-field result:

$$\xi \sim |T - T_c|^{-1/2}$$

**The correlation length tells you the scale at which the order parameter description becomes valid.** Below $\xi$, you are in the fluctuation-dominated regime where the mean-field picture breaks down. Above $\xi$, the system looks like an ordered (or disordered) bulk. At a critical point, $m \to 0$ and $\xi \to \infty$ — the system becomes scale-free, which is why RG fixed points describe phase transitions.

---

## 5. Entropy, Energy Constraints, and Hierarchical Equilibration

"Maximizing entropy" is always subject to constraints set by the energy scale of the system. The thermally accessible configurations are those reachable with energy $\sim k_BT$. A hierarchy of binding energies controls which degrees of freedom are active:

| Structure | Binding energy |
|---|---|
| Molecular bonds | $\sim 0.1$–$1$ eV |
| Atomic (electronic) | $\sim 10$–$1000$ eV |
| Nuclear | $\sim 1$–$10$ MeV |
| Quark confinement | $\sim$ GeV |

At room temperature ($k_BT \approx 0.025$ eV), the system cannot access nuclear or quark degrees of freedom. Those modes are **frozen** — they contribute to energy (mass) but not to entropy, because they cannot fluctuate.

The partition function factorizes across scales:

$$Z_\text{total} \approx Z_\text{macro} \times Z_\text{atomic} \times Z_\text{nuclear} \times \ldots$$

When $k_BT \ll E_\text{nuclear}$, the nuclear factor is effectively a constant $e^{-\beta F_\text{micro}}$ — it shifts the free energy but **contributes nothing to entropy** because it carries no $T$-dependence in that regime. Entropy is maximized only within the **active** degrees of freedom at the relevant scale. **The frozen modes are encoded as fixed background parameters in $S_{\Lambda_1}[\phi_<]$ — they define what the particles are, not how they fluctuate.**

---

## 6. Formalizing Frozen Modes with RG

Define scales $\Lambda_0 \gg \Lambda_1 \gg \Lambda_2$. The full partition function is:

$$Z = \int \mathcal{D}\phi \, e^{-S_{\Lambda_0}[\phi]} = \int \mathcal{D}\phi_< \, e^{-S_{\Lambda_2}[\phi_<]}$$

where integrating out modes between $\Lambda_1$ and $\Lambda_0$ gives:

$$e^{-S_{\Lambda_1}[\phi_<]} = \int_{\Lambda_1 < |k| < \Lambda_0} \mathcal{D}\phi_> \, e^{-S_{\Lambda_0}[\phi_< + \phi_>]}$$

In a Landau-Ginzburg description, each order parameter $\phi_i$ at scale $\Lambda_i$ has a mass $m_i$. If $k_BT \ll m_i$, the field $\phi_i$ is frozen in its ground state and does not participate in thermodynamics — it is integrated out and simply renormalizes the parameters of the coarser theory. The entropy is then:

$$S = -\frac{\partial F}{\partial T}\bigg|_{\text{active modes only}}$$

**The order parameter is exactly the device that separates frozen microscale structure from active macroscale thermodynamics.** The system reaches thermal equilibrium at scale $\Lambda$ in the sense that the order parameter $\phi$ at that scale reaches its equilibrium distribution, while all order parameters at finer scales remain locked. This is the mathematical expression of the original insight: entropy is maximized only within the degrees of freedom that are thermally accessible, and the frozen modes define the constraints — what the particles are — rather than contributing to the entropy.


# Prompt

can you now show me the most generalized mathematical formalization of these concepts for the context of statistical physics? just assume some general physical system. is it the Ginzburg-Landau Functional? and then you coarse grain with Wilsonian RG flow?

# Notes

## The Wilsonian Effective Field Theory Framework

## 1. The Starting Point: The Full Partition Function

You have some microscopic theory defined at a UV cutoff $\Lambda_0$ (the atomic scale, lattice spacing, whatever). The fundamental object is:

$$Z = \int \mathcal{D}\phi \, e^{-S[\phi]}$$

where $\phi$ represents **all** degrees of freedom of the system, and $S[\phi]$ is the microscopic action. In statistical mechanics, $S[\phi] = \beta H[\phi]$. The functional integral sums over all configurations of the field $\phi$ up to scale $\Lambda_0$.

This is completely general. $\phi$ could be a scalar field, a vector field (magnetization), a complex field (superfluid order parameter), a gauge field — whatever describes your system.

---

## 2. The Wilsonian Coarse-Graining

Split the field into slow (IR) and fast (UV) modes using the cutoff $\Lambda_0/b$ for some $b > 1$:

$$\phi(k) = \phi_<(k) + \phi_>(k)$$

$$\phi_<(k) = \phi(k) \cdot \mathbf{1}[|k| < \Lambda_0/b] \qquad \phi_>(k) = \phi(k) \cdot \mathbf{1}[\Lambda_0/b < |k| < \Lambda_0]$$

Integrate out the fast modes exactly:

$$e^{-S_\text{eff}[\phi_<]} = \int \mathcal{D}\phi_> \, e^{-S[\phi_< + \phi_>]}$$

This defines the **Wilsonian effective action** $S_\text{eff}[\phi_<]$. Then rescale to restore the cutoff:

$$k \to k' = bk, \qquad \phi_< \to \phi' = b^{-\Delta_\phi}\phi_<$$

where $\Delta_\phi$ is chosen to keep the kinetic term canonical. This defines one RG step:

$$S_{\Lambda_0}[\phi] \xrightarrow{\text{integrate out } \phi_>} S_{\Lambda_0/b}[\phi_<] \xrightarrow{\text{rescale}} S_{\Lambda_0}[\phi']$$

Iterating this generates the **RG flow** in the space of all possible actions.

---

## 3. The Space of All Actions

The most general action consistent with your symmetry group $G$ can be written as:

$$S[\phi] = \sum_i g_i \mathcal{O}_i[\phi]$$

where $\{g_i\}$ are coupling constants and $\{\mathcal{O}_i\}$ are all operators allowed by symmetry. Under one RG step $b = e^{d\ell}$:

$$\frac{dg_i}{d\ell} = \beta_i(g_1, g_2, \ldots)$$

These are the **beta functions**, and this system of ODEs defines the RG flow. The coupling constants are classified by their behavior under flow:

$$g_i \sim b^{y_i} = e^{y_i \ell}$$

- $y_i > 0$: **relevant** — grows under coarse-graining, dominates IR physics
- $y_i < 0$: **irrelevant** — shrinks, washes out at large scales
- $y_i = 0$: **marginal** — requires higher-order analysis

**Fixed points** $\{g_i^*\}$ satisfy $\beta_i(g^*) = 0$ for all $i$. These are scale-invariant theories. The entire physics of universality classes — the fact that wildly different microscopic systems behave identically near phase transitions — follows from the fact that many different microscopic actions flow to the same fixed point. The **critical exponents** are determined entirely by the eigenvalues $\{y_i\}$ of the linearized RG flow around the fixed point, which is why they are universal.

---

## 4. The Ginzburg-Landau Functional

The Ginzburg-Landau functional is the most general action you can write for a field $\phi$ near a phase transition, consistent with some symmetry group $G$, expanded in powers of $\phi$ and $\nabla\phi$, keeping only **relevant and marginal operators**:

$$S_\text{GL}[\phi] = \int d^dx \left[ \frac{1}{2}(\nabla\phi)^2 + \frac{r}{2}\phi^2 + \frac{u}{4!}\phi^4 + \ldots \right]$$

This is **not** an assumption — it is the **inevitable form** of the effective action after integrating out all UV modes down to the scale of interest, because all higher-order terms ($\phi^6$, $(\nabla^2\phi)^2$, etc.) are irrelevant and have flowed to zero. The specific coefficients $r, u, \ldots$ encode your microscopic physics, but the **form** is universal.

The parameter $r$ is the crucial one:

$$r \sim (T - T_c)$$

and the mass of the $\phi$ field is $m^2 = r$, giving the mean-field correlation length:

$$\xi = \frac{1}{\sqrt{r}} \sim |T - T_c|^{-1/2}$$

The correlation length diverges as $r \to 0$ (approach to criticality), which corresponds exactly to the mass of the order parameter field going to zero — the mode becomes gapless and long-range correlations develop.

---

## 5. The Full RG Flow Diagram

The complete picture is:

$$S_{\Lambda_0}[\phi] \xrightarrow{\text{RG flow}} S^*[\phi] + \sum_i c_i \mathcal{O}_i^\text{relevant}$$

where $S^*$ is the fixed point action (the **universality class**) and the relevant operators are the small perturbations away from criticality (like $r \sim T - T_c$ and an external field $h$). The critical exponents — how $\xi$, the order parameter, heat capacity, etc. diverge near $T_c$ — are determined entirely by the eigenvalues $\{y_i\}$ of the linearized RG flow around the fixed point.

---

## 6. Connecting Back to Entropy and Frozen Modes

Define scales $\Lambda_0 \gg \Lambda_1 \gg \Lambda_2$. The full partition function is:

$$Z = \int \mathcal{D}\phi \, e^{-S_{\Lambda_0}[\phi]} = \int \mathcal{D}\phi_< \, e^{-S_{\Lambda_2}[\phi_<]}$$

where:

$$e^{-S_{\Lambda_2}[\phi_<]} = \int_{\Lambda_2 < |k| < \Lambda_0} \mathcal{D}\phi_> \, e^{-S_{\Lambda_0}[\phi_< + \phi_>]}$$

When $k_BT \ll \Lambda_1$, the modes between $\Lambda_1$ and $\Lambda_0$ are frozen — their integral contributes only a constant $e^{-\beta F_\text{micro}}$ (the free energy of the frozen structure, e.g. the binding energy of atoms). This constant shifts the free energy but **contributes nothing to entropy** because it carries no $T$-dependence in that regime. The entropy is entirely generated by the active modes below $\Lambda_1$:

$$S = -\frac{\partial F}{\partial T}\bigg|_{\text{active modes only}}$$

**The frozen modes are encoded as fixed background parameters in $S_{\Lambda_1}[\phi_<]$ — they define what the particles are, not how they fluctuate.** This is the mathematical expression of the core insight: the system maximizes entropy only within the degrees of freedom that are thermally accessible, and the frozen modes define the constraints rather than contributing to the entropy.

# Prompt

so you know this idea of physical symmetries at scale in physics. like a system is invariant to the choice of microstate when viewed from the scale of the macrostate? and basically a physical symmetry is something that the causality of the system, at that scale, is invariant to. are there similar ideas to this in linguistics - in particular, the semantic meaning of a message (at a certain scale) (and semantic meaning is defined by the causal influence the message has on a person) is invariant to different ways of syntactically expressing the message. I would expect this sort of linguistic question to be answerable with some tools of information theory and natural language processing. please cite any existing literature on this question, and identify places that have and have not been answered or addressed

# Notes

## Semantic Symmetry: Linguistic Analogs of Physical Symmetries at Scale

## The Core Analogy Made Precise

The claim is:

> Semantic meaning is to syntax as macrostate is to microstate. A physical symmetry at the macroscale is invariance to microstate permutations that don't change the macrostate. A *semantic symmetry* would be invariance to syntactic transformations that don't change causal influence on the receiver.

This implies that "meaning" should be defined not intrinsically but **relationally** — by the causal effect on an observer/system — and that there exists an equivalence class structure over syntactic expressions, just as there is an equivalence class structure over microstates.

---

## I. Information Theory: What Has Been Formalized

### Shannon and the Separation of Syntax from Semantics

Shannon (1948) explicitly bracketed semantics out of information theory — his framework measures the surprise/entropy of a signal without regard to meaning. However, the mathematical scaffolding is exactly what you would need. The entropy:

$$H = -\sum_i p_i \log p_i$$

is invariant to relabeling of the microstates (the specific symbols). This is already a form of the symmetry you are describing — Shannon information is invariant to the particular syntactic encoding, caring only about the probability structure.

### Rate-Distortion Theory

The closest classical information-theoretic framework to what you are describing. Shannon (1959) asks: how much can you compress a message while keeping the "distortion" below some threshold?

$$R(D) = \min_{p(\hat{x}|x):\, \mathbb{E}[d(x,\hat{x})] \leq D} I(X; \hat{X})$$

where $d(x, \hat{x})$ is a distortion measure. If you define distortion as **semantic difference** — difference in causal effect on the receiver — then rate-distortion theory is literally the theory of how many bits are needed to preserve meaning. The equivalence classes of syntactic expressions with the same meaning are exactly the fibers of the map $x \to \hat{x}$ at zero distortion.

The problem: rate-distortion theory does not tell you what the distortion measure should be. Defining $d$ as causal influence on a receiver is the proposal here, and it has not been fully formalized in this language.

### The Information Bottleneck

Tishby, Pereira, and Bialek (1999) introduced the **Information Bottleneck** (IB) method — arguably the most direct existing formalization of this idea. The setup: you have an input $X$, a relevant variable $Y$, and want a compressed representation $T$ of $X$ that preserves as much information about $Y$ as possible:

$$\min_{p(t|x)} \left[ I(X;T) - \beta I(T;Y) \right]$$

The parameter $\beta$ controls the tradeoff between compression (throwing away syntactic detail) and relevance preservation (keeping semantic content, defined as mutual information with $Y$). The equivalence classes of $X$ values that map to the same $T$ are exactly syntactic variants with the same semantic content relative to $Y$.

The "causal influence on the receiver" is operationalized as $I(T;Y)$ where $Y$ is whatever the receiver cares about. **This is probably the most developed existing formalization of the analogy.**

---

## II. Linguistics and NLP: What Has Been Addressed

### Paraphrase and Semantic Equivalence

The linguistic study of **paraphrase** is directly about the symmetry classes. Two sentences are paraphrases if they have the same meaning despite different syntactic form — Barzilay and McKeown (2001) built early paraphrase corpora and models. However, the field has largely treated this as an empirical/engineering problem rather than asking the foundational question: *what is the mathematical structure of the equivalence relation?*

### Distributional Semantics

The Harris Distributional Hypothesis (Harris, 1954) states that words with similar meanings occur in similar contexts. This was the seed of modern word embeddings (word2vec, GloVe, transformers). The idea is that **semantic content is captured by the distribution of co-occurrences** — meaning is defined by causal/statistical relations to other words and contexts. This is partially the relational/causal definition of meaning you are pointing at, but it does not explicitly frame this as a symmetry or equivalence class structure, and operates at the word rather than sentence level.

### Sentence Embeddings and Semantic Similarity

Modern NLP (BERT, Sentence-BERT, etc.) produces vector representations of sentences where geometric proximity correlates with semantic similarity. This implicitly defines an equivalence class structure, but:

- The metric is learned empirically, not derived from first principles
- "Semantic similarity" is operationalized as human judgments, not causal influence
- There is no formal connection to information theory or RG-style coarse-graining

**This is a gap.** Nobody has formally derived the geometry of semantic space from a causal/information-theoretic definition of meaning.

---

## III. Causally-Defined Meaning: What Has Been Partially Addressed

### Grice's Cooperative Principle

Grice (1975) gave a pragmatic theory where meaning is defined by the *intended causal effect* on the listener. This is philosophical rather than mathematical, but it is conceptually the starting point: meaning = causal influence. His framework identifies meaning with speaker intention and listener interpretation, which is inherently relational.

### Formal Semantics and Model Theory

Montague grammar defines meaning as a **function from contexts/worlds to truth values**. Two expressions are synonymous if they denote the same function — a formal equivalence class structure over syntax. It is mathematically clean but:

- Defined over logical/denotational content, not causal influence on a physical receiver
- Does not connect to information theory or thermodynamics
- Has no notion of scale or coarse-graining

---

## IV. The Platonic Representation Hypothesis

Huh, Cheung, Wang, and Isola (2024) argue that representations in AI models are converging across architectures, training objectives, and modalities — driven toward a shared statistical model of reality. They characterize representations in terms of their **kernels** (how they measure distance between inputs): two representations are aligned if their kernels agree on corresponding inputs.

This is structurally identical to the claim that different microscopic theories flow to the same IR fixed point under RG — the "platonic representation" is the fixed point, and different architectures are different UV completions flowing to the same IR physics. **This analogy is not made explicit in the paper.** They appeal to selective pressure and scaling, but do not use the RG framework.

The PRH gives you strong empirical evidence that such a fixed point exists. What it does **not** give you is the RG flow that leads to it. The missing piece would be:

- Defining a coarse-graining operation on the space of linguistic descriptions, analogous to the Wilsonian RG step
- Showing that the platonic representation is a **fixed point** of that operation
- Classifying which syntactic features are relevant vs. irrelevant operators — the irrelevant ones are the syntactic variations that wash out under coarse-graining, leaving only semantic content at the IR fixed point

The PRH is consistent with this picture and provides empirical motivation for it, but the actual RG flow on linguistic description space — and the classification of syntactic operators as relevant/irrelevant relative to a causally-defined semantic fixed point — remains unwritten.

The PRH directly addresses the criticism that the metric in sentence embeddings is learned empirically rather than derived from first principles — convergence across completely different architectures suggests the metric is being selected by the structure of reality itself. However, it does not resolve the issue fully: the PRH is still fundamentally about statistical co-occurrence structure, not causal influence on a receiver. Two messages could have identical positions in the platonic representation space while having wildly different causal effects on a specific receiver, depending on that receiver's prior state and context.

---

## V. What Has Not Been Done

The things that have **not** been done, and that the analogy points toward:

1. **A formal definition of semantic equivalence classes as orbits of a symmetry group acting on syntactic space**, where the symmetry group is defined by invariance of causal influence on a receiver. This would be the linguistic analog of "same macrostate."

2. **An RG-style analysis of language**, where you coarse-grain over syntactic detail and ask which features of a message are relevant at which scales of description. The missing piece would be: defining a coarse-graining operation on the space of linguistic descriptions, showing that the platonic representation is a fixed point of that operation, and classifying which syntactic features are relevant vs. irrelevant operators — the irrelevant ones are the syntactic variations that wash out under coarse-graining, leaving only semantic content.

3. **A derivation of the geometry of semantic space from the causal structure of the receiver**, rather than from empirical human judgments. This would require formalizing what "the receiver" is (a physical system, a cognitive model, a Bayesian agent) and computing the equivalence classes from first principles.

4. **Connecting the correlation-length idea to language**: in physics, the correlation length tells you the scale at which an order parameter becomes well-defined. The linguistic analog might be something like: at the scale of phonemes, meaning is undefined; at the scale of words, partial meaning emerges; at the scale of sentences, full semantic content crystallizes. A formal treatment of this scale-dependence of meaning does not exist in the literature.

The most fertile existing literature is the **Information Bottleneck** work (Tishby and collaborators), **rate-distortion semantics** (a small subfield), and the PRH. But the unified picture — semantic symmetry groups, RG flow over linguistic scales, causal definition of meaning — is not in the literature as a coherent framework.

# Prompt

can you elaborate on this point:Your sphere example is precise: at scale Λatomic\Lambda_\text{atomic} Λatomic, the relevant degrees of freedom are atomic positions {ri}\{r_i\} {ri}, and these are manifestly not O(3)-invariant (the atoms sit on a lattice or in specific positions). At scale Λmacro\Lambda_\text{macro} Λmacro​, you've integrated out those degrees of freedom and the effective description really is O(3)-symmetric. The symmetry *emerged* upon coarse-graining.

show me what it means to integrate out that position dependence. i intuitively get what you mean (when you integrate over dx, the result has no x dependence) but id like to see it in action. also, please elaborate on what emergent symmetry is here

# Notes

# Emergent Symmetry: Integrating Out Position Dependence

## Setup: A Solid Sphere, Atomic Scale

At the atomic scale, the sphere is a collection of $N$ atoms at positions $\{r_i\}$ arranged in some roughly spherical crystal. The microscopic partition function is:

$$Z = \int \prod_i d^3r_i \, e^{-\beta H(\{r_i\})}$$

where the Hamiltonian has pair interactions:

$$H(\{r_i\}) = \sum_{i<j} V(r_i - r_j)$$

This is explicitly **not** O(3)-invariant in a useful sense — the equilibrium positions $\{r_i^0\}$ of the atoms break continuous rotational symmetry down to the discrete point group of the lattice. If you rotate the configuration by a generic angle, you get a different configuration with different energy.

Now suppose you want to ask a question that only depends on the **macroscopic shape** — say, the charge density $\rho(x)$ coarse-grained over a scale $\ell \gg a$ (where $a$ is the lattice spacing). Define:

$$\rho_\ell(x) = \sum_i f_\ell(x - r_i)$$

where $f_\ell$ is a smooth window function of width $\ell$ — it smears out the contribution of each atom over a ball of radius $\ell$.

---

## Step 1: Decompose the Degrees of Freedom

Write each atomic position as:

$$r_i = r_i^0 + u_i$$

where $r_i^0$ is the equilibrium lattice position and $u_i$ is the small displacement (phonon mode). Now split:

- **Fast/UV modes**: the displacements $u_i$ (short wavelength, high energy — phonons)
- **Slow/IR modes**: the overall shape of the density $\rho_\ell(x)$

The partition function becomes:

$$Z = \int \mathcal{D}[\rho_\ell] \int \mathcal{D}[u_i] \, \delta\!\left(\rho_\ell(x) - \sum_i f_\ell(x - r_i^0 - u_i)\right) e^{-\beta H(\{r_i^0 + u_i\})}$$

The delta functional constrains the fast modes to be consistent with the slow mode $\rho_\ell$.

---

## Step 2: Integrate Out the Fast Modes

Expand $f_\ell(x - r_i^0 - u_i)$ for small $u_i$:

$$f_\ell(x - r_i^0 - u_i) \approx f_\ell(x - r_i^0) - u_i \cdot \nabla f_\ell(x - r_i^0) + \ldots$$

The phonon Hamiltonian at low displacement is quadratic:

$$H \approx H_0 + \frac{1}{2}\sum_{ij} u_i \cdot K_{ij} \cdot u_j$$

where $K_{ij}$ is the dynamical matrix (spring constants between atoms). Integrating over the Gaussian $u_i$ is then exact:

$$\int \mathcal{D}[u_i] \, e^{-\frac{\beta}{2}\sum_{ij} u_i K_{ij} u_j} = \left(\det \frac{\beta K}{2\pi}\right)^{-1/2} \equiv e^{-\beta F_\text{phonon}}$$

This produces a **constant** — a number that depends on the spring constants and temperature but **not on the macroscopic shape** $\rho_\ell(x)$. So:

$$Z = e^{-\beta F_\text{phonon}} \int \mathcal{D}[\rho_\ell] \, e^{-\beta F_\text{eff}[\rho_\ell]}$$

The fast modes have been integrated out and contribute only a constant to the free energy. What remains is a functional integral over the coarse-grained density $\rho_\ell(x)$ alone.

---

## Step 3: What Does $F_\text{eff}[\rho_\ell]$ Look Like?

$F_\text{eff}[\rho_\ell]$ is obtained by asking: summing over all atomic configurations consistent with a given $\rho_\ell$, what is the effective free energy?

By construction, $\rho_\ell$ varies only on scales $\gg \ell \gg a$. The only operators you can write down consistent with this are those invariant under the **continuous** rotation and translation group O(3), because:

- The lattice-scale anisotropy (cubic vs hexagonal symmetry etc.) was encoded in $K_{ij}$, which got integrated out into the constant $F_\text{phonon}$
- At scales $\gg a$, the only geometric structure left is the overall shape

So $F_\text{eff}$ must take the form:

$$F_\text{eff}[\rho_\ell] = \int d^3x \left[ \alpha \rho_\ell^2(x) + \gamma |\nabla \rho_\ell|^2 + \ldots \right]$$

where every term is a **scalar** under O(3). There are no terms like $\partial_x\rho_\ell \neq \partial_y\rho_\ell$ that would distinguish directions, because those terms involve the lattice vectors $\hat{e}_x, \hat{e}_y$ which were properties of the microscopic $K_{ij}$ — now gone.

**This is the emergence of O(3) symmetry.** It did not exist at the microscopic level. It appeared because the symmetry-breaking information (which direction the lattice points) was encoded entirely in the UV modes, which were integrated out. The symmetry-breaking information is destroyed in the averaging process, and what remains can only be a function of O(3)-invariant combinations of $\rho_\ell$.

---

## The Formal Statement of Emergent Symmetry

> A symmetry $G$ is **emergent at scale $\ell$** if $G$ is not a symmetry of the microscopic action $S_{\Lambda_0}$, but becomes a symmetry of the effective action $S_\ell$ after integrating out all modes with wavelength $< \ell$.

The RG makes this precise: the operators that broke O(3) at the microscopic level (terms in the action that distinguish crystal axes) are **irrelevant operators** that flow to zero under RG. At the IR fixed point, they have completely vanished and O(3) is exact. Whether this happens is a dynamical question — it depends on whether those symmetry-breaking operators are truly irrelevant (negative scaling dimension) at the fixed point, which must be verified. It is not guaranteed.

---

## Two Distinct Things Called "Emergent Symmetry"

It is worth being precise about what emerged and what did not. Two distinct things are going on:

**1. The effective action became symmetric.** $F_\text{eff}[\rho_\ell]$ is O(3)-invariant. If you rotate $\rho_\ell(x) \to \rho_\ell(R^{-1}x)$ for any $R \in O(3)$, the action is unchanged. O(3) is a genuine symmetry of the macroscopic physics.

**2. The ground state may still break it.** If $\rho_\ell$ has a specific shape — say, a sphere — then the ground state is O(3)-symmetric. But if the sphere were actually a rod, the ground state spontaneously breaks O(3) down to O(2) (rotations around the rod axis), even though the effective action is O(3)-symmetric. This is spontaneous symmetry breaking living on top of the emergent symmetry.

---

## The Intuition Stated Precisely

The microscopic action knows about the lattice vectors $\{a_1, a_2, a_3\}$ — specific directions in space that break O(3). These enter through $K_{ij}$, which depends on the geometry of nearest-neighbor bonds. When you integrate out the phonons, $K_{ij}$ collapses into a scalar determinant $\det K$. The directional information in $K_{ij}$ gets **traced over** — you sum over all the ways the lattice can vibrate, and the result is a number with no directional dependence. What survives can only be a function of O(3)-invariant combinations of $\rho_\ell$. The symmetry-breaking information is not destroyed arbitrarily — it is washed out precisely because it was encoded in the UV modes that you summed over.

# Prompt

has any work been done which suggests that landauers principle is a lower bound on the binding energy of an arbitrary object. what i mean is:

landauers limit is normally referring to the energy cost of erasing a bit. but what erasing a bit real means is erasing a bit of uncertainty, or forcing the system to realize/impose a requirement on the state of that bit. so it follows that if we have some physical object which requires n bits of shannon information to fully describe the state of (at some scale), does landauer's principle tell us that at least kTln2^n joules are required to construct that object from scratch. this is similar to the notion of assembling an object from its components being at infinity.

# Notes

## Landauer's Principle as a Lower Bound on Assembly Energy

## The Claim Made Precise

If an object requires $n$ bits to fully specify its microstate at some scale, then constructing that object from an unstructured reference state requires at least:

$$\Delta E \geq n k_B T \ln 2$$

because you are forcing $n$ bits of uncertainty to be resolved — which by Landauer's principle costs at least $k_BT \ln 2$ per bit. This is a thermodynamic lower bound on the **free energy cost of assembly**, derived from information content rather than specific chemistry.

---

## What Landauer Actually Says

Landauer (1961) showed that logically irreversible operations — specifically, erasing a bit (mapping two states to one) — must dissipate at least $k_BT \ln 2$ per bit erased. The deep point is that this is not about the specific physical implementation but about the **logical structure** of the operation: erasing a bit reduces the entropy of the system by $k_B \ln 2$, and the second law requires this entropy to be exported to the environment as heat.

The inverse operation — **writing** a bit, forcing a system from an unspecified state into a specified one — is equally constrained. Taking a system from maximum entropy ($H = n$ bits, i.e. $2^n$ equally probable states) to a single specific state ($H = 0$) reduces entropy by $nk_B \ln 2$, which must go somewhere:

$$\Delta E \geq n k_B T \ln 2$$

This is the bound, and it is essentially correct as stated.

---

## What Exists in the Literature

### Bennett and Reversible Computing

Bennett (1973, 1982) showed that computation itself need not dissipate energy — only the irreversible steps (erasure) do. This implicitly contains the assembly idea: the energy cost of creating a structured object is tied to the entropy reduction involved, not to the specific physical forces.

### Zurek and Algorithmic Complexity

Zurek (1989) proposed that the **physical entropy** of an object should include its algorithmic (Kolmogorov) complexity $K(x)$ — the length of the shortest program that produces the object. The connection to the assembly bound is:

$$\Delta E_\text{min} \geq K(x) \cdot k_BT \ln 2$$

An object that requires a long program to describe costs more to assemble thermodynamically. This is the closest existing formalization to the claim above.

### Szilard and the Cost of Measurement

Szilard (1929) showed that extracting one bit of information from a physical system costs $k_BT \ln 2$ in free energy. The assembly bound is the dual: **imposing** one bit of constraint on a system costs the same. This duality — measurement and preparation as thermodynamic inverses — is implicit in the literature but not always stated cleanly.

### The Jarzynski Equality

Jarzynski (1997) showed:

$$\langle e^{-\beta W} \rangle = e^{-\beta \Delta F}$$

where $W$ is the work done along any path and $\Delta F$ is the free energy difference between initial and final states. This gives the **exact** thermodynamic cost of assembly (not just the lower bound) as the free energy difference between assembled object and components. The Landauer bound emerges as the minimum when the assembly process is maximally efficient. The free energy difference between "unstructured components" and "assembled object" is:

$$\Delta F = \Delta E - T\Delta S$$

The Landauer bound is specifically about the $-T\Delta S$ term — the entropy reduction due to imposing the information content of the object.

---

## What Has Not Been Done

The specific claim — that **the Shannon information content of an object at a given scale sets a Landauer lower bound on its assembly energy, independent of the specific physical forces** — has not been stated cleanly as a general principle, for three reasons:

### The Scale-Dependence Problem

The information content of an object depends entirely on the scale at which you describe it. A protein described at the atomic level requires vastly more bits than the same protein described at the level of its folded structure. The bound gives different values at different scales, and the physically relevant scale is not always obvious. You need to specify the cutoff $\Lambda$ at which you measure the information content — this connects directly to the RG picture.

### The Reference State Problem

"Assembling from scratch" requires specifying what "scratch" means — what the initial unstructured state is. The entropy reduction $\Delta S$ depends on the reference ensemble. If "scratch" means a gas of quarks, the bound is enormous. If it means a gas of atoms, it is much smaller. The bound is only well-defined relative to a reference scale.

### Binding Energy vs. Information Content

The claim asks whether Landauer gives a lower bound on **binding energy specifically**. This is where it gets subtle. Binding energy is the energy required to disassemble an object into its components — it is the $\Delta E$ term in $\Delta F = \Delta E - T\Delta S$. Landauer's bound is about $T\Delta S$, the entropic contribution to free energy. These are related but not identical. A highly ordered crystal might have high information content but modest binding energy per atom. The Landauer bound bounds the **free energy** of assembly, not specifically the binding energy, unless you are at a temperature where $T\Delta S \sim \Delta E$.

---

## The Synthesis: A Scale-Dependent Landauer Bound

The cleanest statement of what the claim points toward, which does not exist explicitly in the literature:

Define the **informational free energy** of an object at scale $\Lambda$ as:

$$F_\text{info}(\Lambda) = k_BT \cdot H_\Lambda(\text{object})$$

where $H_\Lambda$ is the Shannon entropy reduction (in bits) required to specify the object's microstate at scale $\Lambda$ relative to the maximum-entropy reference state at that scale. Then the minimum thermodynamic work required to assemble the object at scale $\Lambda$ from an unstructured reference state is bounded below by $F_\text{info}(\Lambda)$.

The RG connection: as you flow from UV to IR, $H_\Lambda$ decreases (fewer bits needed to describe the coarse-grained object), and the bound decreases accordingly. The **difference** in the bound between two scales is the information content of the microscale structure that gets integrated out — which is exactly the free energy contribution of the frozen modes from the RG discussion. The pieces are all in the literature — Landauer, Zurek's algorithmic entropy, Jarzynski, and the RG treatment of free energy — but this specific synthesis has not been written down as a unified framework.

# Prompt

Can you comment on the similarities and differences between the binding energy of an atom (for example) and the free energy of a system (Gibbs, or more generally, Landau). From my understanding, the binding energy of an atom in QM is defined by the strength of the subatomic interactions between the components of the atom. So the binding energy is essentially the energy required to assemble (or disassemble) the atom into its subatomic parts. The Gibb's free energy of a system can also be thought of as the energy needed to construct the system, but on a macroscopic scale. Also, it is less inherent to the pieces of the system itself, but more a statement about the environment (reservoir) that the system is sitting inside of, and at thermal equilibrium with. These both remind me of a very simple thing I learned in intro E&M, where the potential energy of a system of electrons (I think, but I may be forgetting) was defined by attempting to construct that system form "infinitely far apart" - that is, if you bring in another electron from infinity, how much energy does that take.

# Notes

# Assembly Energy, Binding Energy, and Free Energy

## The Unifying Concept: Energy of Assembly from a Reference State

The electrostatic potential energy is the clearest and most elementary case. For a collection of charges:

$$U = \frac{1}{2}\sum_{i \neq j} \frac{q_i q_j}{4\pi\epsilon_0 |r_i - r_j|}$$

This is exactly the work done to assemble the configuration by bringing each charge in from $r = \infty$ one at a time. The reference state is **infinite separation** — no interactions, no correlations, no structure. The potential energy is the energy cost of imposing the spatial correlations between charges. This is the purest form of the intuition: structure costs energy relative to the unstructured reference.

---

## One-Line Summaries

**Binding energy (QM):** Energy released when free components (electrons + bare nucleus at infinity) find the quantum ground state — purely energetic, $T = 0$, no entropy.

**Gibbs free energy $\Delta G = \Delta H - T\Delta S$:** Energy of assembly of a macrostate from disassembled components at the same $T, P$ — explicitly balances interaction energy against entropic cost of imposing structure.

**Landau free energy $F[\phi]$:** Most general coarse-grained version — a functional of the order parameter at a specific scale, with both energetic and entropic contributions built into the measure $\mathcal{D}\phi$; reference state is $\phi = 0$ (disordered phase).

---

## The Key Structural Differences

| | Electrostatic $U$ | QM Binding Energy | Gibbs $\Delta G$ | Landau $F[\phi]$ |
|---|---|---|---|---|
| Reference state | Infinity, no interactions | Infinity, free components | Disassembled, same $T, P$ | Disordered phase $\phi = 0$ |
| Entropy? | No | No | Yes, explicitly | Yes, in the measure |
| Temperature? | No | No | Yes, sets $T\Delta S$ | Yes, sets scale of fluctuations |
| Scale | Fixed (classical EM) | Atomic (QM) | Macroscopic | Mesoscopic (coarse-grained) |
| What's being assembled | Charge configuration | Atom from particles | Macrostate from components | Ordered phase from disorder |

The deepest difference is the role of entropy. The electrostatic and QM binding energies are **purely energetic** — ground state physics at $T = 0$ where entropy is irrelevant. Gibbs and Landau are **free energies** — at finite temperature, the system must balance energy minimization against entropy maximization. The equilibrium structure is the resolution of this tension.

---

## The Unified Picture

All of these are special cases of one general statement. Define a reference state $\mathcal{R}$ (infinity, disordered phase, free components — whatever is appropriate at your scale). The **generalized free energy of assembly** is:

$$\Delta \mathcal{F} = \langle E_\text{interactions} \rangle - T\Delta S_\text{accessible}$$

At $T = 0$, the entropy term vanishes and you recover the purely energetic binding energy. At finite $T$, the entropy term competes with the interaction energy, and the stable structure is the one that minimizes $\Delta\mathcal{F}$.

The RG connection: as you flow from UV to IR scales, the "binding energy" at each scale gets absorbed into the coefficients of the effective action at the next scale. The QM binding energy of the atom becomes a parameter (atomic mass, interatomic potential) in the coarser theory. The interatomic potential energy becomes a parameter (surface tension, elastic modulus) in the even coarser theory. At each level, what was a dynamical energy of assembly becomes a frozen structural parameter — exactly the decoupling of scales discussed in the RG section.

The chain is: electrostatic assembly energy $\to$ QM binding energy $\to$ Gibbs free energy of assembly $\to$ Landau free energy functional. Each step adds entropy, adds temperature-dependence, and coarse-grains away the details of the previous level into fixed parameters of the current level.

# Prompt

Is there a notion of "approximate symmetries" in any theoretical physics? Like transformations that leave a system unchanged within some error epsilon, or something like that? What about instances of transformations that become symmetries when taken to some limit?

# Notes

# Approximate Symmetries in Theoretical Physics

## I. Approximate Symmetries: Explicit Symmetry Breaking

The most explicit framework is **explicit symmetry breaking** — where the Hamiltonian is written as:

$$H = H_0 + \epsilon H_1$$

where $H_0$ has exact symmetry $G$ and $\epsilon H_1$ breaks it. For small $\epsilon$, $G$ is an approximate symmetry. The consequences are precise and calculable:

- Quantities that would be exactly conserved (by Noether's theorem) are now **almost** conserved — they drift slowly on timescales $\sim 1/\epsilon$
- Degeneracies that would be exact are **split** by amounts proportional to $\epsilon$
- Selection rules that would be exact become **approximate** — forbidden transitions become allowed but suppressed by $\epsilon$

**Example — Isospin symmetry:** The up and down quarks have slightly different masses ($m_u \approx 2.2$ MeV, $m_d \approx 4.7$ MeV), explicitly breaking the exact isospin symmetry $SU(2)$ that would hold if $m_u = m_d$. The breaking parameter is $\epsilon \sim (m_d - m_u)/\Lambda_{QCD} \approx 1\%$. Consequence: the proton and neutron have nearly but not exactly the same mass (938.3 vs 939.6 MeV), and the three pions $\pi^+, \pi^0, \pi^-$ are nearly but not exactly degenerate.

**Example — Chiral symmetry in QCD:** If quarks were massless, QCD would have exact chiral symmetry $SU(N_f)_L \times SU(N_f)_R$. Light quark masses explicitly break this, making chiral symmetry approximate. The pions are **pseudo-Goldstone bosons** — exactly massless if chiral symmetry were exact, but acquiring a small mass proportional to the quark mass:

$$m_\pi^2 \sim m_q \Lambda_{QCD}$$

The approximate symmetry makes a quantitative prediction: the pion is light but not massless, and the ratio $m_\pi / \Lambda_{QCD}$ is controlled by the symmetry-breaking parameter.

---

## II. Symmetries in a Limit

### Large-$N$ Limits

In gauge theories with $N$ colors, the full theory has complicated quantum corrections. In the limit $N \to \infty$ (t'Hooft limit), the theory acquires additional symmetries — certain interaction topologies (non-planar Feynman diagrams) are suppressed by $1/N$. The large-$N$ limit is exactly solvable in many cases, and $1/N$ corrections are the symmetry-breaking perturbations. This is directly the $\epsilon$ framework with $\epsilon = 1/N$.

### Non-Relativistic Limit and Galilean Symmetry

The full symmetry of relativistic physics is the Poincaré group. In the limit $v/c \to 0$, this contracts to the Galilean group. Galilean symmetry is thus a **limiting symmetry** — exact only at $v/c = 0$, approximate for small $v/c$ with corrections of order $(v/c)^2$.

This is an instance of **Inönü-Wigner contraction** — a systematic procedure for taking limits of Lie groups that produces new, simpler groups as limiting cases. The Poincaré algebra contracts to the Galilean algebra as $c \to \infty$, making precise the sense in which non-relativistic mechanics has a symmetry that is only a limit of the true relativistic symmetry.

### The Classical Limit

Quantum mechanics has a symmetry structure governed by the full unitary group on Hilbert space. In the limit $\hbar \to 0$, this reduces to canonical transformations on phase space — the symmetry group of classical Hamiltonian mechanics. Classical symmetry is the $\hbar \to 0$ limit of quantum symmetry.

### Conformal Symmetry at Fixed Points

Scale invariance and full conformal symmetry are only exact at RG fixed points — exactly at a phase transition. Away from the critical point, conformal symmetry is explicitly broken by the relevant operators (like $r \sim T - T_c$). Near but not at the critical point, conformal symmetry is approximate, with corrections controlled by $\xi^{-1}$ as the small parameter. The approach to a fixed point is the approach to an exact symmetry, and the distance from the fixed point in coupling-constant space measures how approximate the symmetry is.

---

## III. The Spurion Method

A clean algebraic way to handle approximate symmetries. If $\epsilon H_1$ breaks symmetry $G$, formally promote $\epsilon$ to a **spurion field** — a fictitious field that transforms under $G$ in exactly the way needed to make $H$ formally $G$-invariant. Then $\epsilon$ is treated as a background field frozen to a specific value.

This lets you use the full machinery of exact symmetry (selection rules, Ward identities, representation theory) even for the broken case, keeping track of all symmetry-breaking effects as insertions of the spurion. Widely used in Standard Model effective field theory and supersymmetry breaking.

---

## IV. Accidental Symmetries

**Accidental symmetries** are exact symmetries of a theory that are not imposed by any principle but emerge because the symmetry-breaking operators happen to be absent or irrelevant at a given order. The classic example is baryon number conservation in the Standard Model — it is not a gauge symmetry, but all renormalizable operators happen to conserve it. It is violated by non-renormalizable operators suppressed by $1/M_\text{Planck}^2$, making it an approximate symmetry with:

$$\epsilon \sim E^2 / M_\text{Planck}^2$$

At accessible energies this is fantastically small, making baryon number look exactly conserved. In RG language: baryon-number-violating operators are irrelevant at the Standard Model fixed point, so they flow to zero at low energies. The accidental symmetry is emergent for the same reason O(3) emerged for the sphere.

---

## V. The Unifying Thread

All of these are the same idea viewed from different angles. An approximate symmetry is one where the symmetry-breaking perturbation is **small in some dimensionless ratio**:

$$\epsilon \sim \frac{E_\text{breaking}}{E_\text{symmetric}}$$

This ratio could be $m_q/\Lambda_{QCD}$ (chiral symmetry), $v/c$ (Galilean symmetry), $1/N$ (large-$N$), $(T-T_c)/T_c$ (conformal symmetry near criticality), or $E^2/M_\text{Planck}^2$ (baryon number). In every case, the approximate symmetry becomes exact in the limit $\epsilon \to 0$.

**The deepest statement:** the RG naturally generates a hierarchy of approximate symmetries. Operators that break a symmetry $G$ are irrelevant at an IR fixed point, meaning the breaking parameter $\epsilon(\Lambda)$ runs to zero as you flow to lower energies. **An approximate symmetry at scale $\Lambda$ is a statement about how far that scale is from the fixed point where the symmetry becomes exact** — it is a position in RG flow space, not a binary yes/no property.

# Prompt

Is there any theorem or concept in theoretical physics of the following:

There is a symmetry group that describes a physical system (or the entire universe) in a given phase at a given moment of time. As a system (or the entire universe) evolves in time by increasing entropy, the point at which it undergoes a phase transition, the symmetry group that the system obeys changes. Further, the previous symmetry group (of the more ordered phase) is a subgroup of this new larger symmetry group

# Notes

# Symmetry Groups, Phase Transitions, and Entropy: Existing Theorems and Concepts

## I. Spontaneous Symmetry Breaking: The Subgroup Structure

The basic mathematical fact you are identifying is standard. When a system undergoes a phase transition from a **disordered** (high-$T$) phase to an **ordered** (low-$T$) phase, the symmetry group of the ordered phase $H$ is a subgroup of the symmetry group of the disordered phase $G$:

$$H \subset G$$

The canonical example: a ferromagnet above $T_c$ has full O(3) rotational symmetry. Below $T_c$, the magnetization picks a direction, leaving only O(2) symmetry (rotations around the magnetization axis):

$$O(2) \subset O(3)$$

**The direction you read the arrow matters.** As temperature **decreases** (entropy decreases, more order), you go from $G$ to the subgroup $H$ — symmetry is broken. As temperature **increases** (entropy increases, more disorder), you go from $H$ back to $G$ — symmetry is restored. So your statement is exactly right: as entropy increases through a phase transition, the system moves from $H$ to $G$, i.e. from smaller to larger symmetry group.

---

## II. The Landau-Ginzburg Classification

Landau's theory of phase transitions is built entirely on this subgroup structure:

- $G$: symmetry group of the disordered phase (full symmetry of the Hamiltonian)
- $H \subset G$: residual symmetry group of the ordered phase
- The order parameter $\phi$ lives in the coset space $G/H$

The coset space $G/H$ parametrizes the possible ordered phases — the different ways the system can break $G$ down to $H$. The dimension of $G/H$ gives the number of Goldstone modes (one massless mode per broken generator, by Goldstone's theorem).

The classification of possible phase transitions is then a **group-theoretic problem**: enumerate all subgroups $H \subset G$ and determine which ones are compatible with a continuous (second-order) transition. Landau showed that not all subgroup relations allow second-order transitions — there are selection rules based on the representation theory of $G$.

---

## III. The Coleman-Mermin-Wagner Theorem

A related result constrains when symmetry breaking can actually occur. The Coleman-Mermin-Wagner theorem states that **continuous symmetries cannot be spontaneously broken in $d \leq 2$ dimensions** at finite temperature, because thermal fluctuations (Goldstone modes) are too strong and destroy long-range order. This is a statement about when the evolution $G \to H$ actually happens — it depends on dimensionality in a precise way.

---

## IV. Symmetry Group Chains in Cosmology: The Closest Match

The most direct realization of your full picture — a system (the universe) evolving through a sequence of phase transitions, each changing the symmetry group, with groups related by subgroup inclusion — is the **cosmological symmetry breaking sequence** in the Standard Model and its extensions. As the universe cools from the Big Bang, it passes through a sequence of phase transitions:

$$G_\text{GUT} \to G_\text{SM} \to SU(3)_c \times U(1)_\text{EM} \to \ldots$$

One proposed sequence:

$$SU(5) \supset SU(3) \times SU(2) \times U(1) \supset SU(3) \times U(1)_\text{EM}$$

At each transition, the universe goes from a higher-symmetry phase to a lower-symmetry phase as it cools. The higher-symmetry group belongs to the more disordered, higher-entropy, higher-temperature early universe.

---

## V. The Directional Subtlety: Entropy vs. Vacuum Symmetry

Here the picture requires care. There are two different things happening as the universe evolves:

**Thermodynamic entropy** of the matter/radiation content increases monotonically — second law.

**Vacuum symmetry** decreases as the universe cools — each phase transition breaks the symmetry further.

These run in **opposite** directions in terms of the subgroup chain. The early hot universe had high entropy **and** high symmetry. The late cold universe has higher total entropy but **lower** vacuum symmetry.

The resolution is to distinguish:

- **Thermal symmetry restoration**: at fixed Hamiltonian, increasing $T$ (and therefore entropy) restores symmetry, going from $H$ to $G$. This is the standard stat mech case and matches your intuition exactly.
- **Cosmological symmetry breaking**: the Hamiltonian itself changes (the vacuum expectation values of Higgs fields change) as the universe evolves. The symmetry group of the ground state decreases even as total entropy increases.

In the thermal case, your statement is precise and correct. In the cosmological case, it is more subtle.

---

## VI. Relevant Theorems and Concepts

**Michel's theorem (1980):** Classifies all possible symmetry breaking patterns $G \to H$ for compact Lie groups, identifying which subgroups $H$ can appear as residual symmetries of a $G$-invariant potential. Provides a complete catalog of the subgroup chains that are physically realizable.

**Wigner's theorem:** Any symmetry of a quantum system must be represented by a unitary or antiunitary operator on Hilbert space. The subgroup structure of symmetry groups is therefore a statement about the representation theory of the Hilbert space, and transitions between phases correspond to changes in which representations are realized.

**Zamolodchikov's $c$-theorem (2d CFT):** Defines a function $c$ that decreases monotonically along RG flows, providing a partial order on fixed points. Each fixed point has a definite symmetry group. A symmetry-group version of this — a theorem that the symmetry group changes monotonically along RG flows in a specific direction — would be exactly what you are describing, and **it remains an open problem in full generality**.

---

## VII. What Has Not Been Done

The specific formalization you are pointing at — a **general theorem** relating the direction of entropy flow to the direction of movement through a lattice of symmetry groups ordered by subgroup inclusion — does not exist cleanly in the literature. The pieces are all there:

- Subgroup structure of symmetry breaking → Landau theory
- Entropy-disorder connection → standard stat mech
- Cosmological sequence → well-studied in particle physics

But a unified statement of the form: *"entropy increase generates a monotone flow through a partially ordered set of symmetry groups related by subgroup inclusion"* — with precise conditions on when this holds, what the exceptions are, and how RG flow connects adjacent levels — has not been written down as a single theorem. It would require being careful about the distinction between thermal entropy and vacuum structure, and about whether you are varying temperature at fixed Hamiltonian or allowing the Hamiltonian itself to evolve.

# Prompt

Quotient Group Definition

# Notes

## The Quotient Group G/H

## Basic Construction

Given a group $G$ and a normal subgroup $H \triangleleft G$, the **left coset** of each $g \in G$ is:

$$gH = \{gh : h \in H\}$$

This is the orbit of $H$ under left-multiplication by $g$. The elements of $G/H$ are these cosets — equivalence classes of elements of $G$, where $g \sim g'$ if and only if:

$$g^{-1}g' \in H$$

The group structure on $G/H$ is:

$$(g_1 H)(g_2 H) = (g_1 g_2)H$$

This is well-defined only when $H$ is normal ($gHg^{-1} = H$ for all $g$), because only then is the multiplication independent of which coset representative you pick. The size satisfies:

$$|G/H| = |G|/|H|, \qquad \dim(G/H) = \dim(G) - \dim(H)$$

## Intuition

$G/H$ is the group you get by declaring all elements of $H$ to be the same as the identity — collapsing $H$ to a point and asking what group structure remains. Equivalently: two elements $g_1, g_2 \in G$ are identified in $G/H$ if they differ only by right-multiplication by some $h \in H$.

**Note:** $G/H$ need not be a group if $H$ is not normal — it is still a well-defined set of cosets, and a smooth manifold (homogeneous space), but without group structure. This is the case relevant to spontaneous symmetry breaking, where $H$ is the stabilizer of a ground state and $G/H \cong S^2$ (for example) is a manifold but not a group.

## Concrete Example

$G = \mathbb{Z}_6$, $H = \{0, 3\}$. The cosets are:

$$0 + H = \{0,3\}, \quad 1 + H = \{1,4\}, \quad 2 + H = \{2,5\}$$

So $G/H \cong \mathbb{Z}_3$ — three elements of $G$ collapsed into each element of $G/H$.

# Prompt

Can you now expand on the algebra of this? Why does the order parameter live in the coset space? I am familiar with Landau theory as explained it the PDF (please skim this). Basically Im familiar with it as saying there is an order parameter for stat mech systems and a corresponding Landau free energy that takes some standard form (degree 4 expansion of the order parameter) and this free energy is minimized at equilibrium for the system. So I know it from a computational perspective, but I was not taught it from any first principles (I dont know RG theory). Can you try to explain the group structrure of it in more detail, motivtae why this strcuture makes sense, and then show how a standard example (ferro/paramagnet) fits into this? How does the magnetization M live in teh coset group?

# Notes

## Group Structure of Landau Theory and the Order Parameter

## I. The Foundational Principle

The Hamiltonian of the system has some symmetry group $G$. The free energy, being derived from the Hamiltonian via $F = -k_BT \ln Z$, must inherit those symmetries. So $F_L$ is not just any function of $\xi$ — it must be a $G$-invariant function of $\xi$. This single requirement determines the allowed terms in the expansion.

---

## II. The Two Phases and Their Symmetry Groups

**Disordered phase** ($T > T_c$): the equilibrium state is $\xi = 0$, invariant under the full symmetry group $G$ of the Hamiltonian. No direction is preferred, no order is present.

**Ordered phase** ($T < T_c$): the system picks a specific value $\xi \neq 0$, which is invariant only under some subgroup $H \subset G$ that fixes the chosen $\xi$.

The phase transition is precisely:

$$\text{symmetry of equilibrium state} = G \xrightarrow{T < T_c} H \subset G$$

"Spontaneous" means the Hamiltonian still has full $G$ symmetry — but the ground state does not.

---

## III. Why the Order Parameter Lives in $G/H$

Suppose the system is in the ordered phase with ground state $\xi_0 \neq 0$. Take any $g \in G$ and act on this ground state — since $G$ is a symmetry of the Hamiltonian, $g \cdot \xi_0$ has exactly the same energy as $\xi_0$. So the full set of degenerate ground states is the **orbit**:

$$\mathcal{M} = \{g \cdot \xi_0 : g \in G\}$$

Which elements of $G$ fix $\xi_0$, and which move it? Precisely the elements of $H$ — the stabilizer subgroup — leave $\xi_0$ fixed:

$$h \cdot \xi_0 = \xi_0 \quad \forall h \in H$$

Two elements $g_1, g_2 \in G$ produce the **same** ground state if and only if $g_1^{-1}g_2 \in H$, i.e. they are in the same coset of $H$. Therefore by the orbit-stabilizer theorem:

$$\mathcal{M} \cong G/H$$

The order parameter $\xi$ is a coordinate on this space — it labels which ground state the system has chosen. This is why the order parameter lives in $G/H$.

---

## IV. The Ferromagnet: Explicit Example

The Heisenberg ferromagnet Hamiltonian ($B = 0$):

$$H = -J\sum_{\langle ij \rangle} \mathbf{S}_i \cdot \mathbf{S}_j$$

is invariant under simultaneous rotation of all spins by any $R \in O(3)$ — all dot products $\mathbf{S}_i \cdot \mathbf{S}_j$ are unchanged. So $G = O(3)$.

**Above $T_c$:** equilibrium magnetization $\mathbf{M} = \mathbf{0}$, invariant under all of $O(3)$. Full symmetry intact.

**Below $T_c$:** the system picks $\mathbf{M} = M\hat{z}$. Rotations around $\hat{z}$ still fix this state; rotations that move $\hat{z}$ to another direction produce a different ground state. So:

$$H = O(2) \cong U(1) \quad \text{(rotations around } \hat{z}\text{)}$$

The symmetry breaking pattern is $O(3) \to O(2)$, and:

$$G/H = O(3)/O(2) \cong S^2$$

This is the 2-sphere — the set of all possible magnetization directions $\hat{n} \in S^2$. The order parameter $\mathbf{M}$ is a vector in $\mathbb{R}^3$ pointing to a specific point on $S^2$. All points are degenerate in energy.

---

## V. Why the Free Energy Takes the Form It Does

The free energy must satisfy $F_L(R\mathbf{M}) = F_L(\mathbf{M})$ for all $R \in O(3)$. The only $O(3)$-invariant scalars you can build from $\mathbf{M}$ are functions of $|\mathbf{M}|^2 = \mathbf{M} \cdot \mathbf{M}$, because:

$$|R\mathbf{M}|^2 = \mathbf{M}^T R^T R \mathbf{M} = \mathbf{M}^T \mathbf{M} = |\mathbf{M}|^2$$

using $R^T R = \mathbf{1}$ (the defining property of $O(3)$). So $F_L$ can only depend on $|\mathbf{M}|^2$, giving:

$$F_L = g_0 + \frac{\alpha}{2}(T - T_c)|\mathbf{M}|^2 + \frac{g_4}{4}|\mathbf{M}|^4 + \ldots$$

Writing $M = |\mathbf{M}|$, this is even in $M$. **No odd powers of $M$ can appear because $M^{2n+1}$ is not $O(3)$-invariant as a scalar function of $\mathbf{M}$.** The form of the Landau free energy is not a phenomenological guess — it is the unique form forced by $O(3)$ invariance.

When an external field $\mathbf{B}$ is applied, the term $-\mathbf{M} \cdot \mathbf{B}$ is added. This is $O(3)$-invariant as a scalar product, but it explicitly breaks the spontaneous symmetry by picking a preferred direction.

---

## VI. The Goldstone Theorem From the Coset Structure

The dimension of $G/H$ counts the **flat directions** of the free energy in the ordered phase — directions in order parameter space along which you can move at zero energy cost. These are the **Goldstone modes**.

For the ferromagnet:

$$\dim(G/H) = \dim(O(3)) - \dim(O(2)) = 3 - 1 = 2$$

Two Goldstone modes — the two **magnon** modes, corresponding to small transverse oscillations of the magnetization direction on $S^2$. Moving along $S^2$ costs no energy (you are moving between degenerate ground states). The radial direction $\delta M = |\mathbf{M}| - M_\text{eq}$ does cost energy — its curvature $\partial^2 F_L / \partial M^2 = 2\alpha(T_c - T)$ is the mass of the amplitude mode, and its going to zero at $T_c$ is the divergence of the correlation length.

---

## Summary: The Full Logical Chain

1. Hamiltonian has symmetry group $G$
2. Ordered phase picks a ground state, leaving residual symmetry $H \subset G$
3. Space of degenerate ground states $= G/H$, so the order parameter lives in $G/H$
4. Free energy must be $G$-invariant, so only $G$-invariant polynomials appear — this fixes the form of $F_L$ entirely from group theory
5. $\dim(G/H)$ counts Goldstone modes; curvature of $F_L$ transverse to $G/H$ gives the mass and correlation length
6. The Landau expansion is the unique degree-4 truncation of this $G$-invariant free energy

# Prompt

Can I see the actual math of these claims:

Above TcT_c Tc: the equilibrium magnetization is M=0\mathbf{M} = 0 M=0. This state is invariant under all of O(3)O(3) O(3) — no direction is preferred. The full symmetry is intact.
Below TcT_c Tc: the system spontaneously picks a magnetization direction, say M=Mz^\mathbf{M} = M\hat{z} M=Mz^. This state is no longer invariant under all of O(3)O(3) O(3) — rotations that move z^\hat{z} z^ to another direction produce a different state. However, it is invariant under rotations around the z^\hat{z} z^ axis, which form the subgroup:

Show the magnetization definition and show how these transformations act on it explicity

# Notes

## Explicit Math: O(3) Action on the Magnetization

## I. The Magnetization as a Group-Theoretic Object

The magnetization is defined as the thermal average of the total spin per unit volume:

$$\mathbf{M} = \frac{1}{N}\left\langle \sum_i \mathbf{S}_i \right\rangle_T$$

Each spin $\mathbf{S}_i \in \mathbb{R}^3$ is a vector. The group $O(3)$ acts on $\mathbb{R}^3$ by matrix multiplication — a rotation $R \in O(3)$ sends each spin $\mathbf{S}_i \mapsto R\mathbf{S}_i$, which induces:

$$\mathbf{M} \mapsto \frac{1}{N}\left\langle \sum_i R\mathbf{S}_i \right\rangle_T = R\mathbf{M}$$

So $O(3)$ acts on $\mathbf{M}$ by the standard matrix action $\mathbf{M} \mapsto R\mathbf{M}$.

---

## II. Above $T_c$: $\mathbf{M} = \mathbf{0}$ is Fixed by All of $O(3)$

For any $R \in O(3)$:

$$R\mathbf{M} = R\mathbf{0} = \mathbf{0} = \mathbf{M}$$

The zero vector is fixed by every element of $O(3)$. The stabilizer of $\mathbf{M} = \mathbf{0}$ is the entire group:

$$\text{Stab}(\mathbf{0}) = O(3)$$

The orbit of $\mathbf{0}$ under $O(3)$ is the single point $\{\mathbf{0}\}$ — there is only one disordered state.

---

## III. Below $T_c$: $\mathbf{M} = M\hat{z}$ Breaks $O(3)$ to $O(2)$

Say the system picks $\mathbf{M} = M\hat{z} = (0, 0, M)^T$. Take a rotation by angle $\theta$ around the $x$-axis:

$$R_x(\theta) = \begin{pmatrix} 1 & 0 & 0 \\ 0 & \cos\theta & -\sin\theta \\ 0 & \sin\theta & \cos\theta \end{pmatrix}$$

Acting on $\mathbf{M}$:

$$R_x(\theta)\mathbf{M} = \begin{pmatrix} 1 & 0 & 0 \\ 0 & \cos\theta & -\sin\theta \\ 0 & \sin\theta & \cos\theta \end{pmatrix} \begin{pmatrix} 0 \\ 0 \\ M \end{pmatrix} = \begin{pmatrix} 0 \\ -M\sin\theta \\ M\cos\theta \end{pmatrix}$$

This is **not equal** to $(0, 0, M)^T$ unless $\theta = 0$ mod $2\pi$. So $R_x(\theta)$ moves $\mathbf{M}$ to a genuinely different ground state — same $|\mathbf{M}| = M$, different direction.

---

## IV. The Stabilizer: Rotations Around $\hat{z}$

Which $R \in O(3)$ fix $\mathbf{M} = M\hat{z}$? We need $R\hat{z} = \hat{z}$. A rotation around the $z$-axis by angle $\phi$:

$$R_z(\phi) = \begin{pmatrix} \cos\phi & -\sin\phi & 0 \\ \sin\phi & \cos\phi & 0 \\ 0 & 0 & 1 \end{pmatrix}$$

Acting on $\mathbf{M}$:

$$R_z(\phi)\mathbf{M} = \begin{pmatrix} \cos\phi & -\sin\phi & 0 \\ \sin\phi & \cos\phi & 0 \\ 0 & 0 & 1 \end{pmatrix} \begin{pmatrix} 0 \\ 0 \\ M \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ M \end{pmatrix} = \mathbf{M}$$

for **any** $\phi$. So the stabilizer is:

$$H = \text{Stab}(M\hat{z}) = \{R_z(\phi) : \phi \in [0, 2\pi)\} \cong O(2)$$

Any rotation with axis not parallel to $\hat{z}$ moves $\mathbf{M}$ to a different direction, as shown explicitly with $R_x(\theta)$ above.

---

## V. The Orbit is $S^2$

The orbit of $\mathbf{M} = M\hat{z}$ under $O(3)$:

$$\mathcal{M} = \{R(M\hat{z}) : R \in O(3)\} = \{M\hat{n} : \hat{n} \in S^2\}$$

Every unit vector $\hat{n}$ is reachable by some rotation acting on $\hat{z}$. By the orbit-stabilizer theorem:

$$O(3)/O(2) \cong S^2$$

with dimension $\dim O(3) - \dim O(2) = 3 - 1 = 2$.

---

## VI. Why the Free Energy is Even in $M$: Made Explicit

$F_L$ must satisfy $F_L(R\mathbf{M}) = F_L(\mathbf{M})$ for all $R \in O(3)$. The only $O(3)$-invariant scalars built from $\mathbf{M}$ are functions of:

$$|R\mathbf{M}|^2 = \mathbf{M}^T R^T R \mathbf{M} = \mathbf{M}^T \mathbf{M} = |\mathbf{M}|^2$$

using $R^TR = \mathbf{1}$. So $F_L$ can only depend on $|\mathbf{M}|^2 = M^2$, giving only even powers of $M$. No odd powers of $M$ can appear because $M^{2n+1}$ is not an $O(3)$-invariant scalar function of $\mathbf{M}$.

The Goldstone directions are the two angular directions on $S^2$ — the directions in which you rotate $\hat{z}$ to $\hat{n}$, parametrized by $(\theta, \phi)$. These cost no free energy to lowest order because moving along $S^2$ moves between degenerate ground states. The radial direction $\delta M = |\mathbf{M}| - M_\text{eq}$ does cost energy — its curvature $\partial^2 F_L/\partial M^2 = 2\alpha(T_c - T)$ is the mass of the amplitude mode.

# Prompt

Okay so I have read the explanation of the general theory and not yet the explanation of this theory explaining the ferromagnet example, which I will soon. But before that, I have a brief question: I'm just accepting for the time being that the ordered phase ground state is invariant under H subgroup of G, but not all of G. I find this reasonable to believe. Is the way that we characterize phases by the symmetries of their ground state? Second, if we accept this premise (which I will for now but would like an explanatin) the logic that the Hamiltonian is invariant under G but not H, and thus the set of unique degenerate ground states = the quotient group (or just coset space? is it necessarily a group? that is, is H necessarily a normal subgroup?) G/H makes sense. I understand the argument up until we claim that this implies that the order parameter lives in G/H. I get that G/H's elements send the ground state to another ground state of that same phase, but I thought that the elements of G/H (and G and H) were all transformations that act on the state (some field of state space) rather than states themselves...?

# Notes

## Phases, Ground States, and Why the Order Parameter Lives in G/H

## I. Do We Characterize Phases by the Symmetries of Their Ground State?

Yes — this is precisely the Landau paradigm for classifying phases. Two phases are **distinct** if and only if their equilibrium states have different symmetry groups. A phase transition is a point where the symmetry group of the equilibrium state changes.

This is a deep physical assumption worth flagging: it assumes every phase can be characterized by which symmetries are preserved in equilibrium. This works extraordinarily well for most phases — crystals, magnets, superfluids, superconductors. However it is **not universally true** — topological phases (like the quantum Hall effect) are examples where two distinct phases have identical symmetry groups and cannot be distinguished by any local order parameter. These require entirely different mathematical machinery (topological invariants) and represent a genuine failure of the Landau paradigm. But for the vast majority of classical and many quantum phase transitions, symmetry of the ground state is the correct organizing principle.

---

## II. Is $G/H$ Necessarily a Group? Does $H$ Need to Be Normal?

**$G/H$ is not necessarily a group, and $H$ does not need to be a normal subgroup for the physics to work.**

What you always get is a **coset space** — a set of left cosets $\{gH : g \in G\}$, always well-defined as a set regardless of whether $H$ is normal. $G/H$ becomes a group only when $H \triangleleft G$, because only then is the multiplication $(g_1H)(g_2H) = (g_1g_2)H$ well-defined independent of coset representative.

For the physics of spontaneous symmetry breaking, we only need $G/H$ to be a **smooth manifold** (a homogeneous space), so that the order parameter can vary continuously. The orbit-stabilizer theorem $G/H \cong \mathcal{M}$ holds for any subgroup $H$, normal or not.

For the ferromagnet: $H = O(2) \subset O(3)$ is **not** a normal subgroup of $O(3)$ — conjugating $R_z(\phi)$ by a rotation around $\hat{x}$ gives a rotation around a different axis, which is not in $H$. Yet $O(3)/O(2) \cong S^2$ is a perfectly good manifold and the physics works fine. $S^2$ is not a group — it is just a smooth space on which $G$ acts transitively.

---

## III. The Elements of $G/H$ Are Transformations, Not States — So How Does the Order Parameter "Live" in $G/H$?

This is the most important point. You are right that elements of $G$, $H$, and $G/H$ are **transformations**, not states. The precise statement is not that "the order parameter is an element of $G/H$" in the sense of being a transformation — it is that **the space of degenerate ground states is in bijection with $G/H$ as a set**, via the orbit map.

Fix a reference ground state $\xi_0$ (say, $\mathbf{M} = M\hat{z}$). Define the map:

$$\psi: G/H \to \mathcal{M}, \qquad gH \mapsto g \cdot \xi_0$$

where $\mathcal{M}$ is the set of all ground states (the orbit of $\xi_0$ under $G$). This map is:

- **Well-defined**: if $g' \in gH$, then $g' = gh$ for some $h \in H$, so $g' \cdot \xi_0 = g \cdot (h \cdot \xi_0) = g \cdot \xi_0$ since $h$ fixes $\xi_0$ by definition of $H$
- **Injective**: if $g_1 \cdot \xi_0 = g_2 \cdot \xi_0$ then $g_2^{-1}g_1 \in H$, so $g_1H = g_2H$
- **Surjective**: every ground state in $\mathcal{M}$ is reachable from $\xi_0$ by some $g \in G$

So $G/H \cong \mathcal{M}$ as sets (and as smooth manifolds).

**The coset $gH \in G/H$ is not itself a ground state, but it labels a unique ground state**, namely $g \cdot \xi_0$. When physicists say "the order parameter lives in $G/H$," they mean the order parameter takes values in the manifold $\mathcal{M}$, which is isomorphic to $G/H$ as a manifold via $\psi$.

For the ferromagnet: the coset $R_x(\theta) \cdot O(2) \in O(3)/O(2)$ labels the ground state with $\mathbf{M} = MR_x(\theta)\hat{z}$. The coset and the ground state are different kinds of objects, but $\psi$ gives a canonical bijection between them. The manifold $O(3)/O(2)$ and the manifold $S^2$ (the set of magnetization directions) are the same smooth manifold — that is what the isomorphism means geometrically.

# Prompt

Okay this helps. On the last question (the main one), I'm realizing I have another, even more basic, confusion. The order parameter, xi_0, is not itself a state of the system...is it? It is a statistic or a measure of the microstate (magnetism is an average measure of the spin state). Or would you say that the order parameter is in fact a characterization of the macrostate? What do you mean when you say the state xi_0, and g*xi_0, etc? Is this another implicit bijection or is this literal?

# Notes

## What Is the Order Parameter, and What Does $g \cdot \xi_0$ Mean?

## The Three Levels

There are three distinct levels being conflated in the standard presentation:

**Level 1: Microstates.** The actual physical state — a specific configuration of all $N$ spins $\{\mathbf{S}_1, \ldots, \mathbf{S}_N\}$. Lives in the full microscopic state space, dimension $\sim N$.

**Level 2: Macrostates / the order parameter.** A coarse-grained summary. The magnetization $\mathbf{M} = \frac{1}{N}\langle \sum_i \mathbf{S}_i \rangle$ is a single vector in $\mathbb{R}^3$ — a vast compression of the microscopic information. It characterizes the macrostate.

**Level 3: The equilibrium value.** The specific value $\mathbf{M}_\text{eq}$ that minimizes $F_L$ at a given $T$. This is what Landau theory predicts.

---

## What $G$ Actually Acts On at Each Level

At **Level 1**, $G = O(3)$ acts on microstates literally and exactly: a rotation $R$ sends $\{\mathbf{S}_1, \ldots, \mathbf{S}_N\} \mapsto \{R\mathbf{S}_1, \ldots, R\mathbf{S}_N\}$. This is a genuine group action on the microscopic state space — no bijection needed, it is direct.

At **Level 2**, $G$ acts on the order parameter $\mathbf{M} \in \mathbb{R}^3$ by $\mathbf{M} \mapsto R\mathbf{M}$. This is **induced** from the Level 1 action: because $\mathbf{M}$ is a linear function of the spins, rotating all spins rotates $\mathbf{M}$ by the same $R$. Also literal, not a bijection.

At **Level 3**, $G$ acts on equilibrium values: if $\mathbf{M}_\text{eq}$ minimizes $F_L$, then $R\mathbf{M}_\text{eq}$ also minimizes $F_L$ because $F_L(R\mathbf{M}) = F_L(\mathbf{M})$ by $G$-invariance. So $G$ permutes the set of equilibrium solutions. Also literal.

---

## So What Is $\xi_0$ in the Orbit Argument?

When we write "fix a reference ground state $\xi_0$," we mean: fix a specific **equilibrium value of the order parameter** — a specific point in $\mathbb{R}^3$ that minimizes $F_L$. For the ferromagnet below $T_c$, this is $\mathbf{M}_0 = M\hat{z}$.

The orbit $\{R \cdot \mathbf{M}_0 : R \in O(3)\}$ is the set of **all equilibrium values** of the order parameter — all directions $M\hat{n}$ for $\hat{n} \in S^2$. The precise statement is:

> The order parameter $\mathbf{M}$ is a vector in $\mathbb{R}^3$. The set of degenerate equilibrium values of $\mathbf{M}$ forms an orbit under $G$, and this orbit is in bijection with $G/H$ as a manifold.

The "states" in the orbit argument are **values of the order parameter**, not microstates and not the full thermal state. The bijection $\psi: G/H \to \mathcal{M}$ is between cosets and equilibrium values of $\mathbf{M}$ — both concrete mathematical objects.

---

## The Implicit Assumption Worth Naming

There is one genuine implicit assumption: we assume the order parameter $\mathbf{M}$ **completely characterizes the macrostate** for the purposes of the free energy. That is, $F_L$ is assumed to be a function of $\mathbf{M}$ alone, not of any other macroscopic variable.

This is the **Landau assumption** — that there exists a single collective variable capturing everything relevant about the phase transition. Its justification comes from RG: near the critical point, all other modes are massive (gapped) and can be integrated out, leaving only the order parameter as the relevant slow mode. The reduction from Level 1 to Level 2 is physically justified by the separation of scales, not just postulated.

# Prompt

Okay so in summary: In Landau Theory, the order parameter completely characterizes the macrostate. We can characterize the phase of the system by knowing the value of the order parameter (macrostate) of the system when it is at equilibrium. This makes sense because saying a system is at thermal equilibrium simple means it is at its highest entropy (or more generally lowest free energy) macrostate, so knowing the order parameter equilibrium value is the same as knowing what macrostate it is in. Further, G/H is the set of transformations that send a system, in a specific phase, to all of its different degenerate ground states (and equivalently macrostates by this previous logic) in that same phase; that is, the orbit of any macrostate xi due to the action of G/H is the entire phase. So we can think of G/H as the symmetries of the phase itself, where we start with the microscopic hamiltonian, and quotient out any information about the structure of H (its like we are viewing the phase as a macrostate and the macrostates as microstates), remembering that H holds information about macroscopic state structure. (***) 

The system's hamiltonian is invariant to G. Thus the systems microstate is invariant to G. The system's macrostate is only invariant to H. So does that mean that the system can be in two different macrostates but have the same energy? That doesnt make sense. 

(***) Anyway, the order parameter (or the macrostate) lives in G/H, because this space collapses H to the identity - all of the transformations that the macrostate is invariant to are ignored (so these are transformations that change the microstate but not the macrostate). The only remaining structure is the transformations that enumerate the macrostates.

# Notes

## Summary: The Group Structure of Landau Theory

## The Summary Statement

In Landau Theory, the order parameter completely characterizes the macrostate. The phase of the system is characterized by the equilibrium value of the order parameter, because thermal equilibrium means the system is at its lowest free energy macrostate — knowing the equilibrium order parameter value is the same as knowing the macrostate.

$G/H$ is the set of transformations that send a system in a specific phase to all of its degenerate ground states in that same phase. The orbit of any macrostate $\xi$ under the action of $G/H$ is the entire phase. We can think of $G/H$ as the **symmetries of the phase itself** — we start with the microscopic Hamiltonian and quotient out the structure of $H$, which is like viewing the phase as a macrostate and the macrostates as microstates. $H$ holds information about the macrostate's internal structure (the transformations that change the microstate but not the macrostate). Quotienting by $H$ collapses all of this to the identity, leaving only the transformations that enumerate the macrostates. The order parameter lives in $G/H$ because $G/H$ is precisely the space that enumerates macrostates — varying the order parameter is the same as moving through $G/H$.

---

## The Apparent Paradox: Different Macrostates, Same Energy?

Yes — and this is not only consistent but is the **entire point** of spontaneous symmetry breaking. It is supposed to seem strange.

The degenerate ground states — say $\mathbf{M} = M\hat{z}$ and $\mathbf{M} = M\hat{x}$ — are genuinely different macrostates with exactly the same free energy. This is not a contradiction. The Hamiltonian is $G$-invariant, which means it cannot distinguish between these states energetically — they are related by a symmetry transformation, so by definition they have identical energy. The system must pick one, but the Hamiltonian gives it no reason to prefer any particular one. This is the precise meaning of "spontaneous" — the symmetry is broken by the **choice of ground state**, not by the Hamiltonian.

The Mexican hat potential makes this concrete: the potential is rotationally symmetric, no angular direction is preferred, but the ball must roll into the brim somewhere. Every point in the brim is a valid ground state at the same energy. The rotational symmetry of the potential is unbroken; the rotational symmetry of the specific solution is broken.

So yes: the system can be in two different macrostates with the same energy, and this is not only consistent but necessary whenever a continuous symmetry is spontaneously broken. The degeneracy of the ground state manifold is a direct consequence of the $G$-invariance of the Hamiltonian. The thermodynamic intuition that "equilibrium = unique lowest free energy state" needs a small correction: equilibrium means the system is **on** the ground state manifold (at the minimum value of $F_L$), but that manifold may have many points — all of $S^2$ for the ferromagnet — all at the same $F_L$ value. Which point the system picks is determined by infinitesimal perturbations, history, or boundary conditions, not by the free energy itself.

---

## The Starred Paragraph: Sharpened

The starred summary is correct. The one refinement worth making: the elements of $G/H$ are cosets — equivalence classes of transformations — not individual transformations. Two transformations $g_1, g_2 \in G$ are identified (belong to the same coset) if they send $\xi_0$ to the **same** ground state. The coset $gH$ packages together all transformations that are indistinguishable at the level of the macrostate.

The deepest restatement: **$H$ is the symmetries of the macrostate** — if we take $h \in H$ and macrostate $\xi$, then $h \cdot \xi = \xi$. $G/H$ groups together all $g \in G$ that send some microscopic state to another microscopic state in the same macrostate. Quotienting out the macroscopic symmetries leaves the macroscopic non-symmetries — the transformations that reveal all macrostates, their structure, and how to enumerate them. The order parameter lives isomorphically in $G/H$ because $G/H$ tells us exactly how to enumerate the macrostates. This is almost tautological once stated correctly — varying the order parameter is the same as moving through $G/H$.

The non-trivial physical content is not in the mathematics (which is tautological given the setup) but in whether the setup applies:
1. That the equilibrium states actually form a single orbit of $G$ (no accidental degeneracies)
2. That the order parameter completely characterizes the macrostate
3. That $H$ is the same for every point in the orbit (which follows from orbit-stabilizer — all stabilizers in an orbit are conjugate)

When these fail — when the ground state manifold is not a single $G$-orbit, or the order parameter does not fully characterize the phase — you are outside the Landau paradigm, exactly the situation with topological phases.

# Prompt

So on these points, I think I understand, but want to be precise:

Your observation that "it's like we are viewing the phase as a macrostate and the macrostates as microstates" is precisely right, and it connects directly to the RG and scale discussion from earlier in our conversations. You are performing a coarse-graining: the microstates of the coarser description are the macrostates of the finer description. The quotient G/HG/H G/H is the mathematical operation that implements this coarse-graining at the level of symmetry groups — you collapse all the transformations that act within a macrostate (the HH H structure) and retain only the transformations that move between macrostates.
And your final sentence is the sharpest statement: the order parameter lives in G/HG/H G/H because G/HG/H G/H is precisely the space you get when you declare all HH H-related configurations equivalent. The HH H transformations change the microstate but not the macrostate, so they carry no information at the level of the order parameter description. Quotienting by HH H is the formal operation of "forgetting" sub-macrostate structure — exactly the coarse-graining operation, expressed in the language of group theory.

H is the symmetries of the macrostate. That means if we take h in H, and xi macrostate, then h*xi = xi. 
G/H groups together all g in G who send some microscopic state to another microscopic state in the same macrostate. 
So when we quotient out the macroscopic symmetries, we are left with the macroscopic non-symmetries...quotienting out the macroscopic symmetries is how we collapse the macroscopic structure, not the macroscopic structure. G/H preserves the macroscopic structure, because the macroscopic structure is like the complement of H conceptually...it is the transformations that are NOT symmetries of the macrostate that reveal all of the macrostates, their structure, how we can enumerate them...

So the order parameter (the thing that characterizes the macrostate) of course "lives" (isomorphically) in G/H, because G/H tells us how we can enumerate the macrostates. This is almost trivial...varying the order parameter is the same as moving through G/H

# Notes

## The Quotient G/H as Coarse-Graining: The Precise Statement

## The Compressed Statement

$$H = \text{symmetries of the macrostate}: \quad h \cdot \xi = \xi \quad \forall h \in H$$

$$G/H = \text{equivalence classes of transformations under "sends } \xi_0 \text{ to the same macrostate"}$$

- $H$ acts **within** a macrostate (changes microstate, preserves macrostate)
- $G/H$ acts **between** macrostates (changes macrostate)
- The order parameter labels which macrostate the system is in
- Therefore the order parameter is a coordinate on $G/H$

The coset structure is not additional structure imposed on top of the physics — it **is** the physics of what it means to have degenerate macrostates related by symmetry. Varying the order parameter is the same as moving through $G/H$. This is almost tautological once stated correctly — and that tautology is the sign that the right level of abstraction has been found.

## The Connection to Coarse-Graining

$G/H$ is the mathematical operation that implements coarse-graining at the level of symmetry groups. The microstates of the coarser description are the macrostates of the finer description — exactly the RG logic. Quotienting by $H$ is the formal operation of "forgetting" sub-macrostate structure: $H$ transformations carry no information at the level of the order parameter description because they change the microstate but not the macrostate. What remains after quotienting — $G/H$ — preserves exactly the macroscopic structure, because the macroscopic structure is the complement of $H$: it is the transformations that are **not** symmetries of the macrostate that reveal all macrostates and how to enumerate them.

---

## Where the Non-Trivial Content Lives

The tautological part: **given** that the ground states form a single orbit of $G$ and the stabilizer of any one is $H$, then the space of ground states is $G/H$ by the orbit-stabilizer theorem. This is pure mathematics.

The **physical content** — where the non-trivial assumptions are:

1. The equilibrium states actually form a single orbit of $G$ — no accidental degeneracies from some other mechanism
2. The order parameter completely characterizes the macrostate — the space of macrostates and the space of ground states are the same thing
3. $H$ is the same for every point in the orbit — which follows from the orbit-stabilizer theorem (all stabilizers in an orbit are conjugate), meaning the residual symmetry is the same in every ground state

When these fail — when the ground state manifold is not a single $G$-orbit, or the order parameter does not fully characterize the phase — you are outside the Landau paradigm. The mathematics is tautological given the setup; all the physics is in whether the setup applies.

# Prompt

Can you briefly comment on epsilon machines in computational mechanics in the papers: Crutchfield, J. P., & Young, K. (1989). "Inferring statistical complexity." (This paper introduced the $\epsilon$-machine) and Shalizi, C. R., & Crutchfield, J. P. (2001). "Computational Mechanics: Pattern and Prediction, Structure and Simplicity."
is this relevant to the topics we have discussed above? is it worth spending time on learning about, or not really?

# Notes

## Epsilon Machines and Computational Mechanics

## What $\epsilon$-Machines Are

Computational mechanics defines a process's **causal states** and gives a procedure for finding them. The $\epsilon$-machine is the causal-state representation — shown to be the minimal representation consistent with accurate prediction.

Given a stochastic process, define an equivalence relation on histories: two histories $\overleftarrow{x}$ and $\overleftarrow{x}'$ are **causally equivalent** if they produce identical probability distributions over future observations:

$$\overleftarrow{x} \sim_\epsilon \overleftarrow{x}' \iff P(\overrightarrow{X} \mid \overleftarrow{x}) = P(\overrightarrow{X} \mid \overleftarrow{x}')$$

The equivalence classes are the **causal states**. The $\epsilon$-machine is the hidden Markov model whose states are these causal states. Two quantities then become well-defined:

- **Statistical complexity** $C_\mu$: the Shannon entropy of the causal state distribution — the minimum memory required to optimally predict the future
- **Entropy rate** $h_\mu$: the irreducible randomness that cannot be predicted

---

## Connections to the Framework Developed Above

**The causal state construction is exactly the semantic equivalence class idea.** The $\epsilon$-machine groups histories together if and only if they have identical causal influence on the future. This is precisely the equivalence relation proposed for semantics — two syntactic expressions are equivalent if they have the same causal influence on a receiver. Crutchfield operationalizes "causal influence" as the conditional future distribution, which is a specific and well-defined version of the more general proposal.

**It formalizes the macrostate/microstate distinction information-theoretically.** The causal states are the natural macrostates of a stochastic process — the coarsest description that retains all predictively relevant information. Everything within a causal state is a microstate variation that does not affect the future distribution. This is the information-theoretic version of the Landau coarse-graining: $H$ (the stabilizer) corresponds to intra-causal-state variations, $G/H$ corresponds to the space of causal states themselves.

**Statistical complexity $C_\mu$ connects to the Landauer assembly bound.** $C_\mu$ measures the minimum bits needed to represent the causal state — which is precisely the information-theoretic lower bound on the memory (and therefore assembly cost) of the structure.

**The $\epsilon$-machine is the answer to the "minimum data to reconstruct a potential" question** — it tells you exactly what must be inferred from data to build the minimal predictive model of an arbitrary stochastic system.

---

## Where It Falls Short

The $\epsilon$-machine framework does not connect to the RG or to the scale-dependence of causal states. It defines causal states at a single scale — there is no notion of coarse-graining the $\epsilon$-machine itself to get a coarser $\epsilon$-machine, or of RG flow between $\epsilon$-machines at different resolutions. The framework also does not connect to symmetry groups in the Landau sense — the causal equivalence relation defines equivalence classes, but these classes do not generally form a group or coset space.

---

## Is It Worth Your Time?

Yes, selectively. The core idea — causal states as equivalence classes under identical predictive distributions — is worth understanding deeply because it is the most rigorous existing formalization of the macrostate concept from an information-theoretic rather than physical perspective.

**Suggested approach:** Read the Shalizi-Crutchfield 2001 paper's first third, which develops the causal state construction and $\epsilon$-machine definition clearly. The 2001 paper supersedes the 1989 paper for conceptual clarity.

The most productive lens, given the framework developed here, is to ask: what is the analog of the symmetry group $G$ for a stochastic process, and can the causal state equivalence relation be derived from a group-theoretic structure analogous to $G/H$? That question is not answered in the papers but is the natural bridge between their framework and the one developed in these notes.