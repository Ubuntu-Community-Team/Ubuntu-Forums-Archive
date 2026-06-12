---
title: "dualboot ubuntu and xp"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by Foresthello on 2007-11-29
hey i was thinking about getting ubuntu back on my harddrive and i was reading about ubuntu 7.10 iv had the disk for a while iit said that you dont need partition magic or anything like that to make a new partition is that true and if it is is there a guide because i dont want to mess up my computer again like last time i installed ubuntu i dont want to delete the xp partition so is there a option in the instalk that lets you choose make a new partition.

---

### Post by src2206 on 2007-11-29
It is necessary to use a partition manager to create a Partition (or at least a free unformatted space of about 4GB and about 1GB for SWAP) to install Ubuntu. You should use GParted (look for a Picture Guide of GParted in my sig).

Ubuntu GRUB will recognize your XP installation automatically so it will be Dual Boot.  You may also install the GRUB in a Floppy, as this will preserve your original windows MBR,so if anything goes wrong you still have your ol' windows to fall back on.

---

