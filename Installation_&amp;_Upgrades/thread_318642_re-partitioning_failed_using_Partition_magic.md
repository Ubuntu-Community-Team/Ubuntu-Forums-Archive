---
title: "re-partitioning failed using Partition magic"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by Physicist on 2006-12-14
Dual boot system with Ubuntu 6.0 and Win XP Home;

5 Partitions, 3 for win, 2 for linux;

Need to install some window stuff which can only be installed on c: where
win OS is installed, have to resize it. Tried to use Partition magic, err pop
up, saying:

Init failed: Error 117
Partition's drive letter cannot be identified


Anybody know what's wrong? Or any other tool(s) to try ?

---

### Post by renzokuken on 2006-12-14
could always try gparted livecd (google it)

not sure how good it is with resizing ntfs but its a great partitioning tool. so much better than partition magic imo

---

### Post by disabled_20220313 on 2006-12-14
As much help as I can be is suggesting a GNU program called "parted"

Its command line, so read about it before using, but doesn't look too complicated for someone to figure out and use.

Suggest you back up your Windows partition and docs onto an external hard drive or DVD-R before preceding.

---

### Post by LDRoamer on 2006-12-14
Gparted live worked well for me when I wanted to re-size an NTFS partition. It took a long time but it worked perfectly.

---

