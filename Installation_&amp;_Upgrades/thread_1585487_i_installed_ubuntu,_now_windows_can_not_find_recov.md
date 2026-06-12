---
title: "i installed ubuntu, now windows can not find recovery part"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by kema_u on 2010-09-30
Hi! I installed to my asus ee 1015 netbook Ubuntu lucid by reseizing the D: part of Windows which was free. Now everythings is fine. But i boot to windows 7 and i press f8 to recovery all hdd or just C: part (it does not matter). But after i click "system restore" it gives this error: "windows can not find the system recovery". but i am sure that i had never touch this part. also i can see this part from linux or windows. i think the problem is windows (after i installed ubuntu) can not understand that there is a part for recover. how can i use this recovery to re-install windows 7 ?

---

### Post by Mark Phelps on 2010-09-30
If what you call the "D part" was REALLY your recovery partition, you likely totally hosed it up resizing it.  And if that is true, there is no way you can restore Win7.

You can provide us some help by opening a terminal in Ubuntu and entering "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list the partitions and show what filesystems are on them.

---

### Post by kema_u on 2010-10-01
D part is not the recovery part. The D part was free and i resize it and i install Ubuntu there. The recoery part is FAT32 and i have never touch it. Just i untick the "hidden" flag, because i need too see what inside the partition. (with Gparted). And after that i set the boot flag from gparted to recovery part, but on windows 7 is seen it on C part.

---

### Post by Sef on 2010-10-01
Applications > Accessories > Terminal

Then copy and paste this code in the terminal:

```
sudo fdisk -l
```

Next copy and paste the results here.

The code will show us what partitions you have.  The recovery partition may have been written over, or it may not be seen.

---

