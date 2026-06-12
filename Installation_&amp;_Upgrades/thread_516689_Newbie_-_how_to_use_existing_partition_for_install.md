---
title: "Newbie - how to use existing partition for install"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by Tony3286 on 2007-08-03
I have gone back and forth reading all about partitioning to HOPEFULLY not have to bother anyone, but I'm still confused.

I have Windows XP on one partition, my "D" drive (on my second partition) is used for backups and I created a 3rd partition (nothing in it) using Partition Magic,answering I'm adding a new operating system that is Linux.

My question is: When I'm installing Ubuntu and get the prompt for partitioning, do I choose the 3rd (Manual) and somewhere in there will allow me to state which partition I want to install Ubuntu? I'm not resizing anything just want to use that partition to install Ubuntu
Also I read something about a swap file. Should I create a 4th partition, before the install,say 2,000MB in size, since I have 1000MB of memory and somehow Ubuntu will use that?

Any help would be GREATLY appreciated

Tony

---

### Post by Steve1961 on 2007-08-03
Yup, choose the manual partition option, select the partition you want to install ubuntu on, select the mount point as /, and select ext3 as the partition type.  Also create the additional swap partition.

---

### Post by Tony3286 on 2007-08-03
Wow, thanks so much for the quick reply. 
How does Ubuntu know how to use that swap file partition I newly created?

---

### Post by Pumalite on 2007-08-03
Ubuntu is very smart.

---

