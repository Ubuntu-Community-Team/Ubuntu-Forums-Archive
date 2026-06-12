---
title: "How to reinstall?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by thewolf32 on 2007-10-18
Hi guys, I want to reinstall EVERYTHING from my messed Ubuntu Feisty installation, even the home directory. Can someone explain me EXACTLY what steps should I take to reinstall Ubuntu succesfully (without touching Windows)?


Thanks

---

### Post by rsambuca on 2007-10-18
If you are happy with the existing partition sizes and just want to re-install overtop of them, just select "Manual Partitioning" at the partitioning step.  Then make sure you direct the installer to put your '/' folder to the same partition it was on already (and make sure you check the box that says to format the partition).  Do the same with your /swap, /home, and any other partitions you may have.  Just make sure you don't format over your XP partition and you will be fine.

---

