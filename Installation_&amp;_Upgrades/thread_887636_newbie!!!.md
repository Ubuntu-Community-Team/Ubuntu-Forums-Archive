---
title: "newbie!!!"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by alchimisto on 2008-08-12
i've just download this: ubuntu-8.04.1-desktop-i386

and i want try linux the first time, and i want conserv window in C:\ and i can sacrify D:\ to linux, and i have to conserv precious data on the others partitions (E, F, G)...

So can i do that and instal this OS without partitionning again my disk???? and how???? and i have to make a dual boot between this two OS...

Thanks in advance

---

### Post by Archmage on 2008-08-12
Burn the iso and put it in, while runing Windows. It should offer you to install without partitioning your harddrives, although it would be run faster on its one partition.

---

### Post by alchimisto on 2008-08-12
> **Archmage said:**
> Burn the iso and put it in, while runing Windows. It should offer you to install without partitioning your harddrives, although it would be run faster on its one partition.
Ok thanks,

so it will be installed only in the D:\ ????

what about the swap partition????

---

### Post by zchenyu on 2008-08-12
C:/ and D:/ are just Windows way of naming drives. You will become more accustomed to saying hda1, hda2 soon ;)

During install, you will be given the option to partition your drive. Assuming you have Windows installed on your entire drive, you should first shrink your Windows partition. That will leave you with unused space on your HD. Then add an ext3 partition on the unused space. You should also create a 2 gb swap space for Linux. Then install Linux on the ext3 partition. This will all make sense in the partition editor ;)

---

### Post by alchimisto on 2008-08-12
> **zchenyu said:**
> C:/ and D:/ are just Windows way of naming drives. You will become more accustomed to saying hda1, hda2 soon ;)

During install, you will be given the option to partition your drive. Assuming you have Windows installed on your entire drive, you should first shrink your Windows partition. That will leave you with unused space on your HD. Then add an ext3 partition on the unused space. You should also create a 2 gb swap space for Linux. Then install Linux on the ext3 partition. This will all make sense in the partition editor ;)
thanks,
if i understood you well, my C:/ will be partitionned ton two partitions to contain windows and Linux, and my D:/ (with 30 GO of space) will be he swap partition.

excuse my ignorance [http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)


any way, the important thing i want is conserving my E, F, G partitions with their data, you see?

---

