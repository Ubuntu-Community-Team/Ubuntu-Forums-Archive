---
title: "Trouble with partitioning."
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by Errorsol on 2007-04-25
I'm trying to dual boot Windows XP and Ubuntu 6.10, I got to the part of the installation where it allows me to partition my HDD in order to dual boot. So I resize my winxp partition, create the swap, ex3, etc. When I click confirm for the program to do those actions it ends up giving me an error saying that it can't resize my NTFS partition. How do I go on about fixing that?

---

### Post by phiphedog on 2007-04-25
It probably can't resize because there is too much data on the partiton or that the data needs to be moved to the start of the partition to allow the free space at the end to be made into other partitions. you can try defragging the windows partition to move all the data to the start of the disk or removing as much unwanted data as possible and then defragging it.

---

