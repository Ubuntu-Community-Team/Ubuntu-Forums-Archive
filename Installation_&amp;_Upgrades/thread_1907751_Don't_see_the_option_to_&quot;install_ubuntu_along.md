---
title: "Don't see the option to &quot;install ubuntu alongside vista&quot;"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by shresthanator on 2012-01-12
He is trying to install ubuntu alongside vista on his laptop. Like he wants to have it dual-boot so that he can switch in between them. 

We are following this: 
[http://www.techspot.com/vb/topic172128.html](http://www.techspot.com/vb/topic172128.html) 

however we get to the step where we are supposed to have the option to "install ubuntu along-side vista". 

It does not give us that option. 

We have the option to "replace vista with ubuntu...." "other...." but not to automatically install vista alongside ubuntu. 

I have installed ubuntu alongside vista and windows7 but I don't think I ever encountered this before. We are just trying to avoid manually re-partitioning the hard-drive. He has 250 gig NTFS right now for his vista, and we don't want to do it manually.

---

### Post by carl4926 on 2012-01-12
From the live desktop
Open a terminal and post the result of

```
sudo fdisk -l
```

---

### Post by Mark Phelps on 2012-01-12
> **shresthanator said:**
> We are just trying to avoid manually re-partitioning the hard-drive. He has 250 gig NTFS right now for his vista, and we don't want to do it manually.

Based on the results of the fdisk command, it's most likely you WILL have to do manual partitioning -- and, if your PC already has the 4 partition limit in place, you will have a LOT more work to do because you'll have to manually REMOVE one to make room.

You can also see the disk partitions if you boot into Vista and use the Disk Management utility.  Count the partitions you see.  IF there are already four of them, that is the maximum allowed.  IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Vista Disk Management utility to shrink the Vista OS partition to make room on the drive.  Vista, like Win7, is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted.  While it may be OK, it's more likely to result in filesystem corruption, which will then render Vista unbootable.

And, after you create some free space, do NOT format it using the Vista Disk Management utility; leave it as free space.  When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by ottosykora on 2012-01-12
@ Mark Phelps

this bad thing with the 4 partitions gets very spread, all new computers I met recently, had this set up.

Soemtimes I think there should be some ***BIG WARNING*** somewhere in the ubuntu installer when such config is found and the user should be stopped somehow to spoil his system.

---

### Post by carl4926 on 2012-01-12
> **ottosykora said:**
> @ Mark Phelps

this bad thing with the 4 partitions gets very spread, all new computers I met recently, had this set up.

Soemtimes I think there should be some ***BIG WARNING*** somewhere in the ubuntu installer when such config is found and the user should be stopped somehow to spoil his system.

Yes
Guess what I do:

Wipe the HD!

---

### Post by Mark Phelps on 2012-01-12
> **ottosykora said:**
> this bad thing with the 4 partitions gets very spread, all new computers I met recently, had this set up.
Yeah ... it's almost like PC vendors want to make it impossible to install a different OS on the PCs they sell!

> Soemtimes I think there should be some ***BIG WARNING*** somewhere in the ubuntu installer when such config is found and the user should be stopped somehow to spoil his system.
There are OTHER things the installer should do as well -- like returning the old "Use largest free space" option that nearly everyone used to set up dual boot systems.  But, Canonical will do what it wants.  The rest of us just have to live with that.

---

### Post by kevdog on 2012-01-12
I usually just install the operating systems on different harddrives -- very easy to do if you have the extra cash for the extra drive.  If you want to do it on one drive, you need to think about how you want to partition your drive first.  You would need at a minimum a /boot partition, a partition for windows, and a partition for ubuntu.  I usually however use a /boot, /, /home, and /swap partions for most of my installs.  You can format the entire disc and make the initial partition with either one of your disc management utilities, or by using gparted utility.  You need to think in advance how big you want to make the partitions depending on how you plan on using the individual os's.  I usually guess wrong -- meaning I find out months later I should have made one partition smaller and another bigger, so hence I usually use two harddrives and over allocate space to avoid this problem.

---

### Post by ottosykora on 2012-01-12
>I usually just install the operating systems on different harddrives --<

yes sure, but many people have just a notebook and need to install it there. And many notebooks today come with 4 primary partitions preinstalled and inexperienced user may just try to shrink one partition , install ubuntu from the installation media using the automatic mode and his system is now trashed definitely.

---

