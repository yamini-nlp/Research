# Research

#### This repository contains my research work, including preprints and supporting materials.
---

### A System-Level Framework for Sentiment-Aware Reflective Writing Systems

**Status:** Preprint · TechRxiv (IEEE) · DOI: 10.36227/techrxiv.177274130.07417144/v1

#### Problem
Sentiment polarity does not reliably indicate user intent, therapeutic need, or correct system response. A journal entry like *"I finally finished everything I needed to do today"* scores positive — but in longitudinal context, it often reflects exhaustion as achievement. Systems that act on S(x) alone get this wrong in predictable, provable ways.

#### Contribution
- Formal definitions: sentiment `S: X → {-1,0,+1}` vs. intent `I: X×C×G×H → A`,where C = context, G = user goals, H = temporal history.
- Proof sketch that S(x) is not a sufficient statistic for intent-aware action selection.
- **Utility-theoretic response selection**: models asymmetric costs of false intervention vs. missed support (C_fp vs. C_fn) and derives 
  optimal decision thresholds — with a worked numeric example (three candidate system responses, expected utility computed under 
  uncertainty over the user's true state z).
- Ethical constraints formalized as action-space restriction, not policy prose.
- 5-layer architecture: Sentiment Detection (L1) → Pragmatic Analysis (L2) → Temporal Pattern Recognition (L3) → Goal-Awareness (L4) → 
  Utility-Based Action Selection (L5).
- Grounded in early-stage prototype deployment observations (reflective journaling context), not synthetic scenarios.

#### Why this matters
Most affective-computing work stops at detection. This paper treats detection as input to a decision problem with real costs on both sides of getting it wrong — and shows how to compute the threshold instead of hand-tuning it.

#### Links
- Paper: [TechRxiv DOI](https://www.techrxiv.org/doi/full/10.36227/techrxiv.177274130.07417144/v1)
- Applied system: [MindNook](https://mindnook-hcj.vercel.app/)
- Repo: [github](https://github.com/yamini-nlp/MindNook-HCJ)

#### Citation
G. S. Y. Devi, "A System-Level Framework for Sentiment-Aware Reflective Writing Systems: Modeling Temporal Emotional Patterns with Interpretability and Ethical Safety," TechRxiv, 2026. DOI: 10.36227/techrxiv.177274130.07417144/v1

---

### Beyond Surface Affect: Why Sentiment Detection Alone Is Insufficient for Intent Interpretation in Human–AI Communication

**Status:** Preprint · TechRxiv (IEEE) · DOI: 10.36227/techrxiv.177274129.99249714/v1

#### Problem
Affect-aware ≠ intent-aware. A user writing *"I think I understand now"* reads as neutral-to-positive to any sentiment classifier — but whether it's a genuine confirmation or a face-saving deflection depends entirely on context, goals, and interaction history that S(x) never sees.

#### Contribution
- **Proposition 1**: proves formally that S(x) ⇏ I(x, C, G, H) — two identical utterances with different (C, G, H) can carry opposite 
  intent while sentiment stays constant. Includes a full proof sketch with a worked counterexample.
- Information-theoretic framing: MI(î; S(x)) < MI(î; I(x,C,G,H)) whenever context carries intent-relevant information that sentiment 
  doesn't capture.
- **Four canonical failure modes** of sentiment-only systems: affective masking, pragmatic inversion (sarcasm), temporal goal drift, and 
  communicative role ambiguity.
- Case observations from **MindNook** (sentiment-aware reflective diary, deployed) — documents where sentiment-first architecture misread 
  positive reframing and exhaustion as stable well-being.
- **MLIM (Multi-Layer Intent Modeling) framework**: 4 layers — Affective Signal (ASL) → Pragmatic Encoding (PEL) → Goal-State Tracking 
  (GSTL, POMDP-style belief update) → Intent Fusion (IFL, entropy-based confidence, triggers clarification requests under high uncertainty 
  instead of committing to a low-confidence intent read).

#### Why this matters
This is the theory paper that the applied work (MindNook, PrepSphere's interview coaching, PrepVision) is built to validate. It's also the one with the strongest formal contribution — the insufficiency proof — so lead with this paper, not the others, when a reader has time for exactly one.

#### Links
- Paper: [TechRxiv DOI](https://www.techrxiv.org/doi/full/10.36227/techrxiv.177274129.99249714/v1)
- Companion paper: *A System-Level Framework for Sentiment-Aware Reflective Writing Systems* (utility-theoretic extension of this framework)

#### Citation
G. S. Y. Devi, "Beyond Surface Affect: Why Sentiment Detection Alone is Insufficient for Intent Interpretation in Human–AI Communication," TechRxiv,2026. DOI: 10.36227/techrxiv.177274129.99249714/v1
  
---

### Comparative Sentiment Analysis of YouTube Transcripts and User Comments

**Status:** Preprint · SSRN · DOI: 10.2139/ssrn.6344859

#### Problem
Transcript sentiment (what a creator says) and comment sentiment (how the audience reacts) are routinely treated as one signal. They aren't.

#### Contribution
- Dual-model pipeline: VADER (lexicon-based) for ASR-derived transcripts, LSTM(supervised) for comments — deliberately different models for 
  text with different linguistic properties (spoken/disfluent vs. informal/sarcastic).
- Pilot study, 12 YouTube videos across 5 domains (political, educational, tech, entertainment, product review).
- **Finding: comments are systematically more positive than transcripts across every video sampled** — mean divergence δ̄ = −48.75 
  percentage points(population SD = 16.1), n=12. No domain reversed this direction in the pilot sample.
- Failure-mode taxonomy: ASR transcription noise corrupting VADER scoring, sarcasm degrading LSTM accuracy on comments.
- Full-stack deployed system: Flask backend, MySQL storage, YouTube Data API v3+ youtube-transcript-api ingestion, interactive 
  visualization.

#### Links
- Paper: [SSRN DOI](http://dx.doi.org/10.2139/ssrn.6344859)
- Repo: [github](https://github.com/yamini-nlp/youtube-sentiment-analysis-ai)

#### Citation
G. S. Y. Devi, "Comparative Sentiment Analysis of YouTube Transcripts and User Comments: Failure Modes and Interpretability in Public Discourse," SSRN, 2026. DOI: 10.2139/ssrn.6344859
