---
title: "gparted not wiping partitions"
date: 2012-11-28
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2012-11-28
I've made a mistake when partitioning a new disk and wanted to just start from scratch.

Thought I just delete all partitiones and create new ones.

Unfortunately, when I hit one particular partition, I always get an error that that device is busy (even though I deleted all partitions and rebooted before).

That particulat partition has a label and I don't understand that when I boot off the live cd, delete all partitions on that disk, create the partitons I want, when I get to the partion in questions, it creates it with the same label.

So it looks that some partition info is not being wiped when deleting the partition.

How can I fix this

---

### Post by darkod on 2012-11-28
If you have an existing swap partition on the disk, the live session mounts it so that it can work faster. You need to unmount it in Gparted first so you can delete it. You can do that by right-click, Swapoff.

The partitions that can't be deleted in Gparted are shown with a keys symbol next to them. If this symbol is shown, you can't delete it and you need to look why the live session is using this partition.

Another way is to use terminal and not Gparted, especially if you want to delete all partitions and start from a blank partition table. Simply use parted and the correct disk label (in this example /dev/sda):
```
sudo parted /dev/sda
mklabel msdos
quit
```

That will create new blank msdos table on /dev/sda. If you need gpt table use mklabel gpt instead of msdos.

You might or might not need a reboot after that, depending if any partition was in use.

---

### Post by lister171254 on 2012-11-28
will give your suggestion a try, but have repartitioned the disk as something other than msdos before, rebooted, repartitioned as msdos and when I get to partion number 5 (i have a primary, an extended, and the first logical, which seems to get me to /dev/sdd5) I still get the old label. In addtion, I cannot get rid of this label.

---

