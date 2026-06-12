---
title: "resize ubuntu partition"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by Mr Nemo on 2009-12-03
I would like to add memory to both the linux partition and the swap partition although I can't figure out how to do it. I installed gparted but it wont let me resize the partitions, and if I use bootit NG it wont let me add to the partition.

---

### Post by lidex on 2009-12-04
To resize your partitions try using the gparted LiveCD. Download and burn to cd. Then boot from the disk. Find it here:
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
Your problem may have been due to the partitions being mounted.

---

### Post by Mr Nemo on 2009-12-04
Worked like a charm, but i takes so long to finish with the operations. Is this because it's ext 4 instead of ntfs?

---

### Post by lidex on 2009-12-04
Resizing always takes longer than creating a new (empty) partition.

---

