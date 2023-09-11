# TIL: 2023-09-11

---

# Topic

- Graph Database

---

# Background

Nowdays I'm struggling to figure out the way for storing tree(especially, `trie` data structure).
Also, I want to insert, delete, and find a string (called `HotDealTitle`) contains which keywords users were enrolled to my system before.

# What I found

There are several conversations about this topic online like [this](https://leetcode.com/discuss/interview-question/system-design/2484704/FAANG-phone-interview-How-to-store-trie-and-tree-efficiently).
But in other articles, many people recommended graph database like `neo4j`.

So I tried to find the graph database, and I hoped if some graph database 'in memory'.

Finally, I found it. The in-memory graph database name is [`MemGraph`](https://memgraph.com/).

- you can click the **MemGraph** for access their landing page

The landing page also show [their discord channel](https://discord.gg/memgraph), so I go there and tell my situtation to them.

> Hi. I'm Inseob, a university student and a prior software engineer. I reached for considering how to manage trie datastructure for searching in memory storage. Currently I'm working on keyword detection system of my toy project. If a title (string type) of an article came in, my keyword detection system finds what keywords are exists in the title.
> I made a trie data structure using keyword list. After queried to the trie, and searched what keywords exist in the title using aho-corasik algorithm. But my system is distributed, so I started to consider..
>
> - how can I store trie into storage (I used Redis)
> - how can I update(insert, delete) the trie how can I query to this trie
>
> In this case, using MemGraph is suitable?

And kindly, the SWE on MemGraph anwered this questions.

> Yes, you can use Memgraph for your system. You can represent the trie as nodes and edges between them (as relationships) where each node would represent a character (with additional information about it if needed) and the nodes would be connected with edges as a transition from one character to another. You can also have a root node to represent a starting point. Then, each keyword will be represented as a path trough nodes and edges, starting from a root node.
>
> Insertion would involve adding the necessary nodes and edges to the database. Deletion would be removing the nodes and edges you don't need/want.
>
> For querying the trie, you can use graph traversal algorithms to find keywords, starting from a root node and traversing the graph based on the characters in the title.

Finally I detailed the plan for enhancing keyword detection system.

First, I will make a measurements for evaluating the performance and utility of all strategies for comparing them.

Next, I will implement all cases.

- the way before I used
- using tokenizer
- using `MemGraph`

Then, see the metrics of them and consider which way is most suitable for my situation.
