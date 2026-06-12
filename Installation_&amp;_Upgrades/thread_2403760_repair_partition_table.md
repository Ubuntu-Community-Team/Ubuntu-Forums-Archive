---
title: "repair partition table"
date: 2018-10-16
forum: Installation &amp; Upgrades
---

### Post by mike442 on 2018-10-16
Hi
i've accidetally deleted not only the mbr but also partition table with
[LEFT][COLOR=#212529][FONT=Inconsolata]# dd if=/dev/zero of=/dev/sdc bs=512 count=1[/FONT][/COLOR][/LEFT]
how to restore the partition table? I've tried gparted but it went on for hours.
on one disk i have Windows and ubuntu partitions and on the other also a hfs+ partition.
many thanks

---

### Post by westie457 on 2018-10-16
Testdisk is possibly the best option. It is available in the repo's. Or with full examples from here. [https://www.cgsecurity.org/wiki/Main_Page](https://www.cgsecurity.org/wiki/Main_Page)

---

