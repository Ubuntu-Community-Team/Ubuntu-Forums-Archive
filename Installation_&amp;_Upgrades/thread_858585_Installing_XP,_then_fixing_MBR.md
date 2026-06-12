---
title: "Installing XP, then fixing MBR"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by Ben Phelps on 2008-07-13
I have dual boot Ubuntu/Vista.  I upgraded to Vista from XP then installed Ubuntu.  I now want to remove Vista and put XP over it.  I want to delete the Vista Partition in Ubuntu and then Install XP in that partition.  I know that XP will overwrite the MBR that lets me boot into Ubuntu or Windows.  Is there a way to fix the MBR without installing Ubuntu over again.

---

### Post by Pumalite on 2008-07-13
This will help:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Ben Phelps on 2008-07-13
Thank you very much.

---

### Post by Pumalite on 2008-07-13
You are welcome. Good luck!

---

### Post by pixelized on 2008-11-22
i have a dual boot xp+ubuntu,however my ubuntu install is on a separate hd..how can fix my mbr after i remove my hd with ubuntu in it?what would i need?

---

### Post by Pumalite on 2008-11-22
Just your XP installation disk: 'h' for Recovery>FIXMBR>FIXBOOT.
Use Super Grub if you don't have an Installation CD:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

