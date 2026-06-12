---
title: "Remove WinXp Partition"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by Flow91 on 2009-11-16
Hello,

I've installed (a long time ago) a WinXp partition (sda1), then an ubuntu one (sda5).

I would like to know how remove the XP one and the extend the ubuntu partition to the all hard disk.

Is there any idea ?

---

### Post by TheHimself on 2009-11-16
Boot your computer with the Ubuntu live CD and then in a terminal run
```
sudo gparted
```

Then you can edit partitions in gparted.

---

