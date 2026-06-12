---
title: "the following error is coming when trying to upgrade ."
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by mahboob218 on 2013-06-24
hi everyone ,


during the updating the error  shown in screenshot is occurring[ATTACH=CONFIG]244095[/ATTACH] ,,can anyone help to fix it ?

---

### Post by steeldriver on 2013-06-24
That error usually means that you have another package manager (synaptic or Software Center) open at the same time - if so close it - if not then some previous package management operation didn't exit cleanly and left a 'stale lock' which you may need to remove manually

---

### Post by mahboob218 on 2013-06-24
hello ,steeldriver 

how i can do it manually ?

---

### Post by Old_Grey_Wolf on 2013-06-24
To remove the lock manually copy and paste this command in a terminal.```
sudo rm /var/lib/apt/lists/lock
```

---

