# Assignment 3. Maze Escape

Student ID: 251433
Name: Sakenov Danial
Group: SE-2540
Maze size (rows x columns): 10 10 

This file is the report. Fill it in as you go. How to start: `START_HERE.md`. The task: `docs/Assignment3.pdf`.

## Program output

The 13 lines your program prints on your data (`java -cp out Main`):

Broken: 71
Kept: 56
Last broken wall: 96
MST cost: 21998
Heaviest broken wall: 738
Path length: 21
DFS visited: 64
Dead ends: 23
Zones: 9
Largest zone: 15
Is DAG: 0
Flow stages: 6
Fastest route cost: 22

My maze:

![maze](output/maze.png)

## Questions

Answer in your own words, two or three sentences each.

Mission 0. What do find and union do, and what makes them fast in your code?
find returns the set representative for an element, and union merges two sets into one. They are extremely fast due to path compression (flattening trees during searches) and union by rank, making operations run in near $O(1)$ amortized time.

Mission 1. Why is Broken always R*C - 1, and Kept always (R-1)*(C-1)?
A grid maze of $R \times C$ cells is a spanning tree, which strictly requires $R \cdot C - 1$ broken walls (edges) to connect all cells without cycles. The remaining $(R-1) \cdot (C-1)$ internal walls must be kept to maintain the grid maze layout.

Mission 2. My MST cost from Kruskal and from Prim, and why they are equal:
My MST cost is [вставьте сюда вашу стоимость MST] for both algorithms. They are equal because both Kruskal and Prim find a Minimum Spanning Tree for the exact same weighted graph, yielding identical minimum total weights.

Mission 3. Why is there exactly one path between two cells? How did you avoid a stack overflow on a huge maze?
Because the maze is a spanning tree (a connected acyclic graph), a unique simple path exists between any pair of cells. To avoid a stack overflow on large mazes, I replaced recursive DFS with an iterative approach using an explicit stack.

Mission 4. Why does the second pass of Kosaraju go on the reversed graph? Why do the slides have no cycle exactly when Zones equals the number of cells?
Reversing edges in the second pass ensures the search is isolated within each Strongly Connected Component (SCC). If every cell forms its own individual zone (Zones equals the total number of cells), no cyclic paths exist between distinct cells.

Mission 5. Why is it enough to go through the zones in the order of their numbers? What does this pass cost?
Processing zones in numerical order works because they are indexed according to a topological sort of the condensation DAG. This linear pass processes each vertex and edge once, costing $O(V + E)$ time.

## AI use

The syllabus requires you to say which AI tools you used and for what. Write the tool (ChatGPT, Copilot, other) and what you asked it: explain an idea, find an error, review code. Write "none" if you did not use any. If you took code or text from a book or a website, give the source here.

## Timing (Mission 7)

Milliseconds, 5 runs each, from `java -cp out Bench`.

| maze | Kruskal | Prim |
|---|---|---|
| 100 x 100 | | |
| 300 x 300 | | |
| 1000 x 1000 | | |

What do the numbers say about how the time grows? Two or three sentences.

## Complexity

n is the number of cells, m the number of walls (or slides). Fill in every algorithm you wrote.

| algorithm | time | space | assumptions |
|---|---|---|---|
| DSU find and union | | | |
| Kruskal | | | |
| Prim | | | |
| DFS | | | |
| Kosaraju | | | |
| Route in the zone graph | | | |

## Before you submit

- data/walls.txt, data/slides.txt and output/maze.png are in the repository.
- `java tools/Check.java` shows all examples right.
- This README is filled in, the program output and the section AI use included.
- The work is pushed to main (at least one commit per mission) and the repository is public.
- The link is attached in Moodle.
