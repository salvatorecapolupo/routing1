# Cammini Minimi — Simulatore di Grafi

Un simulatore didattico, in HTML/CSS/JS puro, per confrontare quattro algoritmi di ricerca su grafo — **Dijkstra**, **BFS**, **DFS**, **A\*** — su un grafo casuale rigenerato ad ogni richiesta.

🇮🇹 [Italiano](#italiano) · 🇬🇧 [English](#english)

---

## Italiano

### Cos'è

Una pagina singola, senza dipendenze da installare (solo un font da Google Fonts via CDN), che genera un grafo casuale di 8–11 nodi e anima passo-passo come ogni algoritmo lo esplora per trovare un cammino da un nodo di partenza a uno di arrivo.

### Algoritmi inclusi

| Algoritmo | Cosa minimizza | Garanzia di ottimalità |
|---|---|---|
| **Dijkstra** | Peso totale del cammino | Sì, sempre (pesi non negativi) |
| **BFS** | Numero di archi (hop), pesi ignorati | Sì, ma solo per il numero di archi |
| **DFS** | Niente — trova *un* cammino qualsiasi | No |
| **A\*** | Peso totale, guidato da un'euristica | Sì (qui l'euristica non è garantita ammissibile, vedi nota nel pannello) |

### L'osservazione centrale: risultati diversi sullo stesso grafo

Cambiando algoritmo **senza rigenerare il grafo**, partenza e arrivo restano gli stessi ma il cammino trovato può cambiare, perché ciascun algoritmo minimizza una grandezza diversa:

- **Dijkstra** e **A\*** trovano sempre il cammino di **peso minimo** — la stessa risposta, ma A\* di solito visita meno nodi grazie all'euristica che lo guida verso l'arrivo.
- **BFS** minimizza il **numero di archi**, non il peso: su un grafo pesato può restituire un percorso con meno passaggi ma peso complessivo maggiore.
- **DFS** non minimizza nulla: restituisce il primo cammino incontrato scendendo in profondità, spesso il più lungo o pesante dei quattro.

Questo è il punto didattico centrale del progetto: "cammino minimo" non è un concetto unico, dipende da *cosa* si sta minimizzando (peso, hop, o nessuna delle due). Il modo più diretto per vederlo è passare da un tab all'altro sullo stesso grafo e confrontare il cammino evidenziato e il riepilogo finale (peso totale, numero di passi).

### Struttura della pagina

- **Area grafo (SVG)**: nodi come cerchi "carta" su sfondo blueprint a griglia, archi con etichetta del peso.
- **Controlli**: selezione algoritmo, nuovo grafo, avvia/pausa, passo singolo, riavvolgi, velocità.
- **Pannello laterale**: per l'algoritmo selezionato, tre schede — *Spiega facile*, *Storia*, *Pseudocodice*.
- **Riepilogo risultato**: cammino trovato (lettere dei nodi) e la metrica minimizzata da quell'algoritmo.

### Come si usa

Basta aprire `cammini-minimi.html` in un browser moderno, non serve un server né build tool.

1. Scegli un algoritmo dalle schede in alto.
2. Premi **Avvia** per l'animazione automatica, oppure **Passo** per avanzare manualmente.
3. Premi **Nuovo grafo** per generarne uno diverso.
4. Cambia algoritmo mantenendo lo stesso grafo per confrontare i risultati (vedi sopra).

### Codice sorgente

Tutto in un unico file (`cammini-minimi.html`): CSS con variabili per il tema, generazione del grafo (albero di copertura + archi extra per creare cicli), quattro funzioni che producono la sequenza di passi dell'animazione, e un piccolo motore di playback.

### Licenza

Nessuna dipendenza a licenza restrittiva; usa e modifica liberamente per uso didattico.

---

## English

### What it is

A single HTML page, no dependencies to install (only a Google Fonts import via CDN), that generates a random graph of 8–11 nodes and animates step by step how each algorithm explores it to find a path from a start node to an end node.

### Algorithms included

| Algorithm | Minimizes | Optimality guarantee |
|---|---|---|
| **Dijkstra** | Total path weight | Yes, always (non-negative weights) |
| **BFS** | Number of edges (hops), weights ignored | Yes, but only for edge count |
| **DFS** | Nothing — finds *a* path | No |
| **A\*** | Total weight, guided by a heuristic | Yes (here the heuristic isn't guaranteed admissible, see note in the panel) |

### The central observation: different results on the same graph

Switching algorithm **without regenerating the graph** keeps start and end fixed, yet the path found can change, because each algorithm minimizes a different quantity:

- **Dijkstra** and **A\*** always find the path of **minimum total weight** — the same answer, though A\* usually visits fewer nodes thanks to the heuristic guiding it toward the goal.
- **BFS** minimizes the **number of edges**, not the weight: on a weighted graph it can return a path with fewer hops but higher total weight.
- **DFS** minimizes nothing: it returns the first path it stumbles on while going as deep as possible, often the longest or heaviest of the four.

This is the project's core teaching point: "shortest path" isn't a single concept — it depends on *what* you're minimizing (weight, hop count, or neither). The clearest way to see it is to switch tabs on the same graph and compare the highlighted path and the final summary (total weight, number of steps).

### Page structure

- **Graph area (SVG)**: nodes as "paper" circles on a blueprint-style grid background, edges labeled with their weight.
- **Controls**: algorithm selector, new graph, play/pause, single step, rewind, speed.
- **Side panel**: for the selected algorithm, three tabs — *Easy explanation*, *History*, *Pseudocode*.
- **Result summary**: the path found (node letters) and the metric that algorithm minimizes.

### Usage

Just open `cammini-minimi.html` in a modern browser — no server or build tool needed.

1. Pick an algorithm from the tabs at the top.
2. Press **Avvia / Play** for automatic animation, or **Passo / Step** to advance manually.
3. Press **Nuovo grafo / New graph** to generate a different one.
4. Switch algorithm while keeping the same graph to compare results (see above).

### Source code

Everything lives in one file (`cammini-minimi.html`): CSS with theme variables, graph generation (spanning tree + extra edges for cycles), four functions producing the animation's step sequence, and a small playback engine.

### License

No restrictively-licensed dependencies; use and modify freely for teaching purposes.
