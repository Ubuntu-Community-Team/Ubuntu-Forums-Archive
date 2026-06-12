---
title: "formatting/partitioning flash drive problem"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by yiannit on 2008-03-03
i'm trying to partition my flash drive or even format it but when i run fdisk  it shows this 

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?      379950      937327   570754815+  72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?       82368     1027695   968014120   65  Novell Netware 386
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?      913029     1858355   968014096   79  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?     1409025     1409052       27749+   d  Unknown
Partition 4 does not end on cylinder boundary.


i cant do anything to my drive

---

### Post by Pumalite on 2008-03-03
Use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.

---

