---
title: "Fresh install but keep soft raid"
date: 2023-07-29
forum: Installation &amp; Upgrades
---

### Post by iunsure on 2023-07-29
Hey Peeps

I have got a system which has 2 SW raid arrays. I think I need to reinstall the OS, is it possible to keep the arrays?

---

### Post by MAFoElffen on 2023-07-29
Always may sure you have good backups, so you have a fallback.

Yes. Install with the Ubuntu 22.04.2 Server Live Installer. The partitioner in that installer is "file manager" aware. When you get to the screen previous to the partitoner, where is asks if you want to erase and use the full disk... or other options, at the bottom will be and option to do "other"... The partitioner will start and you will see your RAID Arrays, partitions within it and your RAID Members. 

I use that Installer, then install whatever I want on top of that. Server, Desktop, etc.

One method to do a {repair} is to install the same release over the top of existing, without reformatting it.

---

