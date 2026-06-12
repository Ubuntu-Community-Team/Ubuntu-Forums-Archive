---
title: "Can't even boot on recovery mode. Used search no luck..."
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by Atum on 2006-09-25
I have an escalating problem. I updated brezzy to dapper. Stupid of me. ](*,) First i got na X-something problem that i tried to solve using the help of fine members of the ubunto forum. But it only got worse (probably due to my inexperience) 

 After trying to deal with the X-something problem, i ended up with  two ubuntos in GRUB, dont know why. And none of them work, not even the recovery mode. So... i'm stuck. I just wanna go back to good old breezy and not have to format my hardrives again.

both recovery modes give out the same issue. only they get there in diferent ways. And there are solutions to this in the forum, but they need me to use comand like sudo and all that, wich I cant cause i dont even have a comand line...

the problem is this:

(after allot of segmentation falts)

ALERT! /dev/hdb5 does not exist. Droping to a sheel 

BusyBox v1.01 (etc...)

/bin/sh: can't access tty; job control turned off
# 





Please help me .

I use ubunto for my blender renders (save almost half the time) so, this really is a big set back for me.

Thank you

---

### Post by Atum on 2006-09-26
Anyone? Should I kust reinstall? if so how do i get rig of the previous versions and use the existing disk partitioning?

---

### Post by az on 2006-09-26
> **Atum said:**
> 

(after allot of segmentation falts)

ALERT! /dev/hdb5 does not exist. Droping to a sheel 


If it were not for the segmentation faults, I would ask if you made some changes to your partitions?

In regards to the seg faults, maybe you have a bad disk?  Or maybe you only partially upgraded?  Are you able to boot into a former kernel's recovery mode?  Can you use the Breezy install disk to boot your system in rescue mode (you use the kernel on the cd and then it chroots you into an installed system)

---

### Post by Atum on 2006-09-26
I tried to use the dapper cd (alternate) to boot nad give me a hand, but no luck, it's all chinese anyway. I'm starting to think the best option is to format the partition and install it all again

---

