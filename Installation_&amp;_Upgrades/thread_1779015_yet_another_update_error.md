---
title: "yet another update error"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by janno92 on 2011-06-09
[ATTACH]194694[/ATTACH]

what should i do?i cant update 
and i dont know how to report

---

### Post by drs305 on 2011-06-09
You most likely have a corrupt package list. Open a terminal and run this command, but make sure you type it correctly! It will remove the lists, which will be recreated when you run the third command:

```
sudo rm -vf /var/lib/apt/lists/*  # Removes the package lists, including any which are corrupted.
sudo apt-get clean 
sudo apt-get update
```

---

### Post by janno92 on 2011-06-09
> **drs305 said:**
> You most likely have a corrupt package list. Open a terminal and run this command, but make sure you type it correctly! It will remove the lists, which will be recreated when you run the third command:

```
sudo rm -vf /var/lib/apt/lists/*  # Removes the package lists, including any which are corrupted.
sudo apt-get clean 
sudo apt-get update
```

oh thank you, it solved my problem, thank you so much...

---

