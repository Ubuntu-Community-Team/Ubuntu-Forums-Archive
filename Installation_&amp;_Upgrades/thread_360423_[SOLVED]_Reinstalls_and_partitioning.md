---
title: "[SOLVED] Reinstalls and partitioning"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by Hopalong on 2007-02-13
I needed to reinstall Edgy from the CD. left the partitions as they were , and chose to manually select them. The swap partition was O.K., but selecting the original root partition gave Warning no root file system.  The fix seems to be to go back into gpedit (using the CD system) and reformat the partition (getting rid of the old system).
This seems odd, since the install process says it will reformat the partition anyway.

---

### Post by housam on 2007-02-13
Reformat the 2 partition using Gparted tool.

---

### Post by guru1 on 2007-02-13
What i believe you need to do depends majorly on whether you want to keep your old files, or whether you want to delete everything.

in case you want to delete everything, then what you need to do is to get to the partition manager in the install process and choose to manually work on the partitions. Select the partitions in Question and delete them, i would recomend you delete both the root and the swap partitions.. Thereafter you should go on and automatically partition the free space.. and your install should go on just fine.

---

### Post by Hopalong on 2007-02-14
Yes! of course I should have said Gparted and not Gpedit.  But why should I have to, when the screen with mount options offers that option anyway?

---

### Post by housam on 2007-02-14
> **Hopalong said:**
> Yes! of course I should have said Gparted and not Gpedit.  But why should I have to, when the screen with mount options offers that option anyway?

It is the same. Do it in the mount log . It'll be ok.

---

