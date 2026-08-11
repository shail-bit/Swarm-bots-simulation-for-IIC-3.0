# Self-Assembling Structures — Decentralized Swarm Algorithms for Emergent Architecture

Exploring how thousands of simple, identical robots — each following only three local rules and **no central controller** — can coordinate to construct complex structures like towers and bridges.

## Idea

Centralized robotics doesn't scale: a single controller is a network bottleneck, a single point of failure, and needs expensive always-on infrastructure. This project instead simulates a **decentralized swarm**, where every agent senses only its nearby neighbors and reacts with three weighted forces:

| Rule | Behavior |
|---|---|
| **Separation** | Steer away from nearby neighbors to avoid collisions and crowding |
| **Alignment** | Match heading and speed with the local group direction |
| **Cohesion** | Steer toward the average position of nearby neighbors |

```
P(t+1) = P(t) + V( w₁·Separation + w₂·Alignment + w₃·Cohesion )
```

Complex, coordinated structures emerge from the interaction of many simple agents — the same principle behind bird flocks and fish schools (Reynolds' Boids, 1987) — extended here with a **stigmergy-style build rule**: agents that sense an unclaimed build site fly there carrying material, place it, and head back out for the next one, so the structure is built by the swarm rather than being the swarm.

## Repository structure

```
.
├── simulation/
│   └── swarm-sim.html       # Self-contained interactive browser simulation (no dependencies)
├── presentation/
│   └── Self-Assembling-Structures.pptx   # Project slide deck
└── README.md
```

## Running the simulation

No build step, no server, no dependencies — it's a single static HTML file.

1. Download `simulation/swarm-sim.html`
2. Open it in any modern browser (Chrome, Firefox, Edge)

**Controls:**
- **Free Flock** — pure separation / alignment / cohesion flocking
- **Build Tower** / **Build Bridge** — bots ferry blocks to unclaimed build sites and construct the structure while continuing to flock
- Sliders adjust agent count and the weight of each of the three rules in real time

## Current scope vs. roadmap

| Stage | Scope |
|---|---|
| **Now** | Small swarms (dozens of agents) self-assembling simple 2D shapes in simulation |
| **Next** | Scale to 1,000+ agents in 3D; add obstacle avoidance and richer target geometries |
| **Later** | Physical micro-robot prototypes for tiny bridges / towers under the same rule set |

## Why decentralized

| | Centralized | Decentralized swarm |
|---|---|---|
| Scaling | Bottlenecks at the server | Scales linearly with swarm size |
| Failure tolerance | One failure halts the system | Tolerates partial agent failure |
| Infrastructure | Needs comms + compute towers | Works with zero infrastructure |
| Deployability | Impractical off-grid | Fits Mars / disaster-zone use |

## License

MIT — see [LICENSE](LICENSE).
