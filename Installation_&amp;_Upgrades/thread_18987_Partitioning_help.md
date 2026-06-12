---
title: "Partitioning help"
date: 2005-03-09
forum: Installation &amp; Upgrades
---

### Post by MrFunster on 2005-03-09
Hi.

I have a 40GB HD which at present is exclusively ubuntu warty, plus swap; EXT3.

I want to split this into 2 20GB partitions so I can play with other distros.

If I run gparted I see all the partitions have a (locked) padlock in the column next to Filesystem (I believe this is because gparted is trying to work on a mounted disk, so I know I can't actually do anything whilst running warty).
I ran knoppix and then QTparted, but all operations were greyed.
How can I resize and split partitions, if no operations are permissible?

---

### Post by az on 2005-03-10
"I ran knoppix and then QTparted, but all operations were greyed."

Are yousure that nothing was mounted - including your swap?

You can use your warty install cd to partition your drives.  Just boot from it, make your way to the partitionner and select the partition you want to change and make your changes.

---

### Post by MrFunster on 2005-03-10
[QUOTE=azz]"."

Are yousure that nothing was mounted - including your swap?

.[/QUOTE]
Knoppix doesn't mount any drives until you click on them IIRC so nothing was mounted as far as I am aware.

---

### Post by strawberry on 2005-03-10
[QUOTE=MrFunster]Knoppix doesn't mount any drives until you click on them IIRC so nothing was mounted as far as I am aware.[/QUOTE]
 After booting Knoppix maybe you should run QTparted from terminal as root.

---

### Post by MrFunster on 2005-03-10
[QUOTE=strawberry]After booting Knoppix maybe you should run QTparted from terminal as root.[/QUOTE]

that's exactly what I did

---

### Post by Xian on 2005-03-10
[QUOTE=MrFunster]How can I resize and split partitions, if no operations are permissible?[/QUOTE]
The Ubuntu installer uses parted for partitioning just as QTparted does. 
Good idea to use that to partition your HD.

I'm not entirely certain that resizing existing Linux partitions is enabled in Knoppix.

---

