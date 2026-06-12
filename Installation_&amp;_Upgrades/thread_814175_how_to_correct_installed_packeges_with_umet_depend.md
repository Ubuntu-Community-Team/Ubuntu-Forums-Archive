---
title: "how to correct installed packeges with umet dependancies"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by dr_gauravsuneja on 2008-05-31
i tried to install bluemarine on ubuntu it tried to install sun jre but it hangs for 5 hrs while configuring it .since then i am unable to install any thing like any *.deb file it say synaptic is already running and it says


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

how to use this command .it must be used in terminal kinldy write a scpript and my software update manager also shows red exclamation mark too

---

### Post by Rocket2DMn on 2008-05-31
You need to run
```
sudo dpkg --configure -a
```
from terminal: Applications->Accessories->Terminal

---

### Post by robertchahine on 2008-05-31
> **rocket2dmn said:**
> you Need To Run
```
sudo Dpkg --configure -a
```
From Terminal: Applications->accessories->terminal
+1

---

