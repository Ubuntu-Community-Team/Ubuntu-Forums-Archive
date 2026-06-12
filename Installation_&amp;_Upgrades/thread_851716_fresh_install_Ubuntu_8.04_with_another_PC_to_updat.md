---
title: "fresh install Ubuntu 8.04 with another PC to update."
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by yosumi on 2008-07-06
hi i have installed ubuntu 8.04 on a laptop and it's fully updated. 

i plan to install ubuntu 8.04 on another PC but knowing the update manager would kill another 250MB bandwidth after fresh install i was wondering if it's possible to migrate my laptop's exisiting updates. 

thanks

---

### Post by Rocket2DMn on 2008-07-06
You can copy the files from /var/cache/apt/archives to the folder on the other machine, then run the update/upgrade.  That should use the updated packages without downloading them.  Any updates not their will be downloaded.

---

### Post by zvacet on 2008-07-07
Use [aptoncd]("http://aptoncd.sourceforge.net/") to do that.You don´t have to download it from site.It is in synaptic.

---

### Post by yosumi on 2008-07-07
hey thanks everyone. nice tips.

---

