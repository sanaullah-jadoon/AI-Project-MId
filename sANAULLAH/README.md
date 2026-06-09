# AI-Based Network Pathfinding & Attack Simulation System
COMSATS University Islamabad | CSC 262 — Artificial Intelligence**  
Instructor: Zeenat Zulfiqar | Due: may 30, 2026

---

# Project Structure

```
 AI_Attack_Path_Simulation/
├── AI_Attack_Path_Simulation.ipynb   ← Main Colab notebook (submit this)
├── GUI_Attack_Simulation.html        ← Interactive GUI (open in browser)
├── main_algorithms.py                ← All 7 algorithms (pure Python)
├── visualizations.py                 ← Matplotlib graph visualizations
└── README.md                         ← This file
```


# How to Run

### Option 1 — Google Colab (Submission)
1. Go to [colab.research.google.com](https://colab.research.google.com)
2. Upload `AI_Attack_Path_Simulation.ipynb`
3. Click **Runtime → Run All**
4. Export as PDF: **File → Print → Save as PDF**

# Option 2 — Interactive GUI
1. Open `GUI_Attack_Simulation.html` in any modern browser
2. Select an algorithm from the left sidebar
3. Click **RUN** to visualize the attack path
4. Click **RUN ALL** to populate the comparison table

# Option 3 — Local Python
```bash
pip install networkx matplotlib
python main_algorithms.py
python visualizations.py
```

---

# Network Topology

| Node | Label | Type |
|------|-------|------|
| 0 | Entry Workstation | Start (Attacker) |
| 1 | Router | Router |
| 2 | Switch | Switch |
| 3 | Firewall | Firewall |
| 4 | Web Server | Server |
| 5 | Mail Server | Server |
| 6 | Internal Network | Network |
| **7** | **Database** | **TARGET (Goal)** |
| 8 | Admin Workstation | Workstation |
| 9 | Backup Server | Server |

**Edge weights** = vulnerability/risk score (lower = easier to exploit)

---

# Algorithms Implemented

| # | Algorithm | Category | Optimal? |
|---|-----------|----------|----------|
| 1 | BFS | Uninformed | No (hops) |
| 2 | DFS | Uninformed | No |
| 3 | UCS | Informed | **Yes** |
| 4 | A* | Informed | **Yes** (admissible h) |
| 5 | Hill Climbing | Local | No (local maxima) |
| 6 | Minimax | Adversarial | N/A |
| 7 | Alpha-Beta Pruning | Adversarial | N/A (more efficient) |

---

## Sample Results

| Algorithm | Path | Cost | Nodes Exp | Time(ms) |
|-----------|------|------|-----------|----------|
| BFS | 0→1→3→6→7 | 19 | 10 | ~0.03 |
| DFS | 0→1→2→4→6→3→8→7 | 23 | 8 | ~0.01 |
| **UCS** | **0→1→3→8→7** | **15** | 10 | ~0.03 |
| A* | 0→1→2→4→6→8→7 | 16 | 7 | ~0.01 |
| Hill Climbing | 0→2→4→6→7 | 20 | 4 | ~0.01 |
| Minimax | 0→1→3→6→7 | 19 | 95 | ~0.08 |
| Alpha-Beta | 0→1→3→6→7 | 19 | 66 | ~0.05 |

UCS finds the true optimal path (cost=15). A* explores fewest nodes. Alpha-Beta reduces Minimax node evaluations by ~30%.
