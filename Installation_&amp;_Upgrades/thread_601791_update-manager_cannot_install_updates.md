---
title: "update-manager cannot install updates"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by insane_alien on 2007-11-03
hey guys. normally, i update by terminal(i just type in update and my password since i made a script for it.) but i used the update0manager on a whim and realised that it cannot install the updates. 

clicking on the install updates button just does nothing at all.

aptitude, synaptic and everything else work fine though.

---

### Post by zvacet on 2007-11-03
```
sudo aptitude update && sudo aptitude upgrade
```

---

