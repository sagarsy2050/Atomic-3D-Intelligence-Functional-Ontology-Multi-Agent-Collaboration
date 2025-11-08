
# Atomic 3D + Functional Ontology + 50 AI Agents – ULTIMATE DRUG DISCOVERY ENGINE

**THE ONE THAT WORKS EVERYWHERE**

Generates **low-energy 3D conformers**, computes **Gasteiger charges**, **dipole**, **PMI**, **asphericity**, embeds **per-atom 3D coordinates + charges** into a **full OWL ontology**, and launches **50+ atomic-level LLM agents** via Ollama for deep SAR insights.

**Uses of “Atomic 3D + Functional Ontology + 50 AI Agents – Ultimate Drug Discovery Engine”**

1.Drug Discovery & Design: Accelerates identification of promising molecules by generating 3D conformers, computing quantum and geometric properties, and predicting molecular activity.

2.Structure-Activity Relationship (SAR) Analysis: Uses 50+ AI agents to analyze atomic, bond, and molecular parameters to provide mechanistic insights and design suggestions.

3.Ontology & Knowledge Management: Builds a full OWL ontology embedding molecular and atomic features, enabling structured storage, querying, and reasoning across datasets.

4.Data Visualization & Reporting: Interactive visualization of molecules (3D) and tabular properties via py3Dmol and Streamlit, supporting hypothesis testing and presentations.

5.Research & Education: Provides a modular, transparent pipeline for teaching cheminformatics, AI-assisted molecular analysis, and computational chemistry workflows.

Integration & Automation: Can run in Jupyter, terminal, Docker, or GPU-enabled setups, enabling high-throughput screening and automated analysis pipelines.
### Features
- ETKDGv3 → MMFF → UFF optimization chain (bulletproof)
- 50+ specialized atomic agents with real LLM reasoning
- Full OWL/RDF ontology with 3D coordinates per atom
- Real Gasteiger charges, dipole, PMI, asphericity
- Works in Jupyter, terminal, Docker
- Auto-generates sample data
----
+----------------------------+
|  Streamlit UI / Backend    |
|  - File upload             |
|  - Visualization (py3Dmol) |
|  - Controls (run, params)  |
+------------+---------------+
             |
             v
+----------------------------+
| Orchestrator / Pipeline    |
| - input validation         |
| - conformer scheduler      |
| - QM job submitter         |
| - agent coordinator        |
+----+----+----+-------------+
     |    |    |
     |    |    +--> Ontology Builder (owlready2) -> OWL file
     |    |
     |    +--> PySCF Runner (INDO) -> QM outputs (HOMO/LUMO, Mulliken)
     |
     +--> RDKit Conformer Engine -> 3D conformers, Gasteiger charges
           -> per-atom parameters
----
flowchart LR
  subgraph UI [Streamlit / UI]
    A1[Upload SMILES/CSV] --> A2[Controls / Params]
    A2 --> A3[3D Viewer (py3Dmol)]
  end

  subgraph Core [Orchestrator Pipeline]
    B1[Input Validator] --> B2[Conformer Scheduler]
    B2 --> B3[RDKit Conformer Engine]
    B3 --> B4[Feature Extractor (charges, dipole)]
    B4 --> B5[Agent Coordinator]
    B5 --> B6[Ollama Client]
    B4 --> B7[Ontology Builder (owlready2)]
    B5 --> B8[Storage (CSV/JSON/OWL)]
    B3 --> B9[PySCF Runner (INDO) - optional]
  end

  A1 --> B1
  B6 -->|LLM responses| B5
  B7 --> B8
  B9 --> B5
----
SMILES/CSV -> Parse -> Molecule objects
Molecule -> RDKit conformer generation -> 3D coordinates (+charges)
3D + charges -> Feature extraction -> per-atom & per-molecule params
params -> (a) PySCF INDO calculations -> QM properties
       -> (b) Ontology builder -> OWL triples
params + QM -> Agent prompts -> Ollama -> Agent outputs (insights)
All outputs -> Persist (CSV/JSON/OWL) + Visualization
----
flowchart TB
  Input[SMILES / CSV] --> Parser[Parser -> RDKit Mol objects]
  Parser --> Conformers[RDKit: 3D conformers + charges]
  Conformers --> Features[Feature extraction: dipole, PMI, atoms]
  Features --> QM[PySCF INDO -> HOMO/LUMO, Mulliken]
  Features --> Onto[Ontology Builder -> OWL]
  Features --> Agents[Agent Manager -> prompts]
  QM --> Agents
  Agents --> Ollama[Ollama / LLMs]
  Ollama --> Insights[Agent outputs]
  Insights --> Storage[(CSV / JSON / OWL)]
  Storage --> Viewer[py3Dmol / Streamlit UI]
---
----
----
### Quick Start
```
pip install -r requirements.txt

python atomic_3d_ontology_50_agents.py --ollama --model llama3.2


'''

Step 1: Run this structure locally 
atomic-3d-ontology-50-agents/
├── README.md
├── requirements.txt
├── data.csv
├── atomic_3d_ontology_50_agents.py
├── agents/
│   └── __init__.py
├── ontology/
│   └── builder.py
├── conformers/
│   └── generator.py
├── utils/
│   └── ollama_client.py
├── config/
│   └── agents.json
└── .gitignore

