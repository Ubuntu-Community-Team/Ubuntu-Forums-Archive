---
title: "Problems SATA/IDE system does not boot"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by rocketman768 on 2007-01-22
I installed 6.10 via cd onto /dev/hdb. It is an IDE drive. I have XP on an sata drive. Looked like I didn't have a choice where to install grub, but it said installed to "hd0". My boot config in the bios at the time was:

DVD
SATA
IDE

I then changed the order so that IDE was above SATA, and guess what? Didn't boot to linux, but XP instead. I am downloading the alternate install CD now. Has anyone else had this problem?

---

### Post by rocketman768 on 2007-01-22
Changed the IDE drive to be bootable with the alternate install disk. That's all it was.

---

