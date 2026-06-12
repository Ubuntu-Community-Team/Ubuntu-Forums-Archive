---
title: "Can I remove a kernel without Synaptic?"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by secondstage on 2008-11-04
Whenever I go to install a program, from synaptic, or aptitude etc, an error: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. ". From the searching that I've this is because there is not enough room in the boot partition. Because the kernels cannot be removed from synaptic etc, how in the world could I remove them? 

PS. Repartitioning from Live CD take forever, so please make that a last resort.

---

### Post by taurus on 2008-11-04
Maybe these would help.

```
sudo apt-get clean
sudo apt-get autoremove
sudo dpkg --configure -a
sudo apt-get update
```

---

