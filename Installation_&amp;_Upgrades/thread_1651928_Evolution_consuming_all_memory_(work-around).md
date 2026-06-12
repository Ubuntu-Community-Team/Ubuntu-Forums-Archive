---
title: "Evolution consuming all memory (work-around)"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by i6p0 on 2010-12-23
I just installed Meerkat (10,10) from an old version 8.10.  I exported my Evolution database and re-imported into the new 10.10.  Then, every time I would switch between viewing two folders, I'd lose somewhere between 6 Mbytes and 10 Mbytes of RES memory (according to top).  It didn't take long to slow the machine to a crawl and force me to power down in order to reset it.  

I found that turning off the plugin "Templates" eliminated this symptom completely.  I don't know what "Templates" does for me, but unchecking this option cured the memory leak problem.

---

