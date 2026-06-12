---
title: "Dual boot, 2 HDDs and partition problems"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by afzalnaj on 2010-07-08
Two of the partitions on my HDD are showing as "unknown" in Gparted.

This was after I modified the cylinders in testdisk to correct the boundaries.

Is there a way to restore the working structure back?

---

### Post by afzalnaj on 2010-07-08
help plz...and sorry about the wrong section. The post was different before.

---

### Post by oldfred on 2010-07-08
Testdisk is the normal way to repair partition issues. Did you go back into it and see what it says:

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by afzalnaj on 2010-07-08
yep, this morning i just did a deep scan with testdisk on the windows hdd. Recovered the useful Windows and Games partitions and deleted the "system reserved" one.

just waiting on Gparted to resize a partition then I'll rebuild BCD in the windows part and hopefully that'll solve it.

Guess the solution was within my grasp. :s

Thank you for the help though :) I appreciate it.

Although IF the path that I am hoping will work with Grub2 to boot Windows doesn't work...I will post here again but I hope it will since it's supposed to be the same as "boot with the first/second hdd"

---

### Post by afzalnaj on 2010-07-13
in the end...I figured it was useless to hope Windows can solve its problems.

Backed up drive C, reinstalled windows, booted with sdb (thanks to Bios Boot Partition) and everything is running fine :)

---

