---
title: "[SOLVED] Can't get synaptic package manager to work. :("
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by Nova1989 on 2008-05-30
i can't get the synaptic package manager to work. i was trying to install "wine" when i got this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by Oldsoldier2003 on 2008-05-30
> **Nova1989 said:**
> i can't get the synaptic package manager to work. i was trying to install "wine" when i got this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

from a terminal
```
sudo dpkg --configure -a
```

---

### Post by Nova1989 on 2008-05-30
ok, it did a few things after i typed that, i tried the synaptic package manager and got this message:
sun-java6-bin
Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)

it said this was a broken package. i tried to get rid of it but i couldn't. i believe this resulted from my trying to install virtualbox to run windows.

---

