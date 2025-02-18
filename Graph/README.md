# Graph

## Introduction
### Composition:
    1. Vertex (Node)
    2. Edges
  ### Types
    1. Directed 
    2. Undirected
  ### Representation
    1. Matrix (A_ij)
        Suitable for dense graph
        Highly inefficient if the matrix is sparse
    2. Adjacency list
      array of vertices
      array of edges
      each edge points to its end points
      each vertex points to edges incident on it
  
  ## Min cut problem
    
    Input: an undirected graph G = (V, E), parallel edges allowed
    
    Goal: Compute a cut with fewest number of crossing edges
    
  ### Applications
    1. Computer vision: Image segamentation
    2. Identify network bottle neck
    3. Community detection in social networks
  
  ### Random Contraction Algorithm
  
    While there are more than 2 vertices:
      pick a remaining edge (u, v) uniformly at random
      merge u and v into a single vertex
      remove self-loops
    return cut represented by final 2 vertices
  
  ## Graph search
  
  ### Goal:
    1. Find everything findable given a starting vertex
    2. Don't explore anything twice
  ### Generic algorithm
    Given graph G, vertex s
    - Initially s explore, all other vertices unexplored
    - While possible:
        choose edge (u, v) with u explored and v unexplored
        mark v explored
  ### Breadth first search (BFS)
    O(M+N) time using a queue (FIFO)
    - Explore nodes in "layers"
    - Can compute shortest paths
    - Can compute connected components of an undirected graph
  ### Depth first search (DFS)
    O(M+N) time using a stack (LIFO)
    Recursive algorithm
    - Explore aggressively like a maze, only backtrack when necessary
    - Compute topological orderingof directed acyclic graph
    - Compute connected components of directed graph
  ### Strongly Connected Components
  
  ### Find Shortest Path - Dijkstra's algorithm
    Each edge is associated with a length which is not necessarily 1. 
    Length of edge must not be negative (Causing the algorithm to fail)
    Find the shortest path for every vertex in the graph from a starting vertex s
    Algorithm:
        X[s]: Vertices that has been processed so far
        A[s]: Length of shortest path for processed vertices
        B[s]: Shortest path for processed vertices
        While X does not cover all vertices:
            among all edges (v,w) with v in X and w not in X
            pick w that minimizes A[v]+length(v,w)
            add this w to X
            add shortest path length of w to A
            add shortest path of w to B
        
