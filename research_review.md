# Research Review

In this lesson, we have learned some classical plannings. I would like to describe one more classical planning, partially order planning which is referred many times in AIND chapter 10.
 and other next two more planing, HPS and Fast Downward Planning(FDP).

 Partial order planning was developed to solve some very simple problems,
such as the Sussman anomaly, which were not able to be solved by previous plannings.
 In contrast to Partial order planning, previous plannings are called total ordered planning or linear planning(AIND 10.6).
 Totally ordered planning considers that each action is executed sequentially. 
 The Sussman Anomaly problem has some goals state. 
 When a linear planner finds the shortest path for one of the goal, the planner must invalidate the goal state
  to find the shortest path for another next goal[[1](https://en.wikipedia.org/wiki/Noninterleaved_plannin)].
  To solve this problem, partial order planning can find each goal's optimal path independently.
  Partial order planning has another advantage, having smaller search space than total order planning.
 Until forward-search planning with excellent heuristics was developed, Partial order planning was considered to be the best approach for
  planning problems with independent subproblems(AIND 10.4.4).
   Therefore, next, I'm going to introduce to the examples as forward-search plannings with excellent heuristics, HPS, Fast Downward Search(FDP), and LAMA.

HSP is forward search planning with the hill-climbing heuristic function. At every step, one of the best children is selected for
expansion and the same process is repeated until the goal is reached[][2](http://www.sciencedirect.com/science/article/pii/S0004370201001084)].
HSP considers consecutive plateau. If non-decremented state continues to some extent, the search is terminated and restarted.
HSP was entered into the AIPS98 Planning Contest, and affected other competitors in terms of forward search planner with heuristic function.

Similar to HSP, FDP is also forward search planning with heuristic function.
 For computing its heuristic function, FDP uses hierarchical decompositions of planning tasks,
 called the causal graph heuristic[[3](http://gki.informatik.uni-freiburg.de/papers/helmert-jair06.pdf)].
 The causal graph heuristic computes its heuristic estimates by solving subproblems of the planning task.
 In other wards, starting from top-level goals, the algorithm recurses further and further
down the causal graph until all remaining subproblems are basic graph search tasks.
Fast Downward solves a planning task in three phases, translation, knowledge compilation, and search.
In translation, PDDL 2.2 input is translated into binary form.
In knowledge compilation, The causal graph is generated, which is hierarchical dependencies between the different state variables.
  In search, three different search algorithms are used.
FDP itself won the satisficing track at the International Planning Competition in 2004.

LAMA is based on the FDP, inheriting the overall structure and large parts of the functionality from that planner[[4](http://jair.org/media/2972/live-2972-5181-jair.pdf)].
 Compared to FDP, LAMA replaced causal graph heuristic with heuristic which is derived from landmarks.
 Landmarks are propositional formulas that have to become true at some point in every plan.
  LAMA uses landmarks to direct search towards those states where many landmarks have already been achieved.
LAMA won the satisficing track at the International Planning Competition in 2008.

## references
  1. https://en.wikipedia.org/wiki/Sussman_Anomaly
  2. http://www.sciencedirect.com/science/article/pii/S0004370201001084
  3. http://gki.informatik.uni-freiburg.de/papers/helmert-jair06.pdf
  4. http://jair.org/media/2972/live-2972-5181-jair.pdf