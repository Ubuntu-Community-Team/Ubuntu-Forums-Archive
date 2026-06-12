---
title: "Setting Up Partitions"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by bparham on 2007-03-07
I'm having trouble installing Dapper with the correct partitions. I'm not quite sure what is going on. I'm trying to set-up a 12 GB Root, 1.5 GB Swap, and 26.5 GB Home. The first time I attempted the install the Root partition didn't form properly, it was missing several folders. The second go around the system is working, however I know have a 12GB Swap and a 26.5GB Main with no home. 

Is there anything that I can do to correct this without re-installing for the third time?

If not, any idea what I'm doing wrong? I double checked when I assigned the partitions everything looked good then. Would it help if I completely reformated the drive prior to installation? If so, how should I do this?

---

### Post by Kateikyoushi on 2007-03-07
Well you could try to resize those partitions from the live disc and the move /home but I think a fresh install is a cleaner solution.

Did you set the mount points correctly during installation ?

---

### Post by bparham on 2007-03-07
To the best of my knowledge, yes the mount points were set correctly. I was thinking about re-formating the drive into one large blank space with the Live CD. The attempting a fresh install.

---

### Post by dstew on 2007-03-07
One stumbling block I have seen in the partitioning process comes when you are asked to select mount points. You need to check the little box next to the partition to format a new partition. It is not enough just to select a mount point. You also have to check the box.

---

### Post by bparham on 2007-03-07
Yeah, I checked those too... I've about decided I'm going to go at this a new way. I'm going to let the install program do a complete wipe of the hard drive. This process worked for me before. Once it is operational I'm going to set-up a new /home partition. 

I've got a 30GB hd, how much space should I leave for root? i'm thinking 12GB, I don't want to overdo it, but I certainly want to make sure that I have enough space to add any program that I may want to add.

---

