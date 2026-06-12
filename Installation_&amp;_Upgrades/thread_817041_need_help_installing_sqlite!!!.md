---
title: "need help installing sqlite!!!"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by nadier on 2008-06-03
i dont know where to start. its sitting on my desktop extracted. can anyone tell me what to do from here? by the way this is my third day using linux so i might not exactly be the most knowledgeable person here

---

### Post by mxg01 on 2008-06-03
How did you install it? It should not end up on your desktop.

The best way to install it is via Synaptic. Using the menus go to  System - Administration - Synaptic Package Manager. When Synaptic loads search for sqlite and click the box next to it. Select mark for installation, then click Apply on the toolbar. It will install correctly then.

If you don't see it then you'll need to enable installing from the 'universe' repository. Go to System - Administration - Software Sources, then click the box next to Community Maintained...(universe). 

To use it you need to open a terminal session and type ```
sqlite3
``` 

To get help:
```
sqlite3 --help
```

SQL Lite has a good website with documentation.

---

