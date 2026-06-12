---
title: "Ubuntu 9.10 Partition Merge"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by phillipjennings5 on 2010-03-23
Can anyone walk me through merging my partitions?
i have a 100 GIG HDD in my 64bit computer
16gigs is NTFS(whatever that is) for Windows 7
15 Gigs is Linux Ext4(Version 1.0)
and 66 Gigs of Unallocated space i was first trying to have windows and linus both use the 66gigs together but i gave up](*,) . neway. 

I want to merge 30 of the 66 gigs to my 15 Gig Linux Partition. anyone know how? and please make a easy because i dont know ish about computers...

---

### Post by stlsaint on 2010-03-24
You may want to look into [LVM]("http://en.wikipedia.org/wiki/Logical_volume_management").

---

### Post by jackocleebrown on 2010-03-24
Hello,

First of all - backup everything important to you in-case anything goes wrong!

You'll need a liveCD to boot to - perhaps you have one from when you installed ubuntu? Put this in the CD drive and restart the computer - with a little luck you will boot from the CD drive no the hard disc. This means that your HD will be unmounted and you will be free to change the partitions. Assuming you are using an ubuntu live CD there is a program under "system"-"administration" I think that it is called "Partition Editor" (otherwise might be GParted) Run this program and with a little luck you should see a graphical representation of you HD showing each of the partitions that you have. Have a good look and check that it is showing the info that you expect before you continue. Identify which partition is your 15 gig linux install. If you are lucky the extra 66gig will be next to it. Assuming this is the case click on the partition and then choose resize/move. A menu will pop up and you can use this to change the size of the partition. When you are happy click resize/move. At this point triple check everything - make sure that you only have 1 operation pending (look at the info text at the bottom). when you are satisfied everything is ok click on apply - the program will then resize the partition as you requested. Once it has finished shutdown, remove the CD and reboot.

Have a look here for some more info: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Partitioning is an easy way to loose data if you get it wrong so be careful and double check everything.

Good luck!

---

### Post by phillipjennings5 on 2010-03-25
alright guys thanks for the help im going to try the Live cd ad Gparted way.

---

### Post by Mark Phelps on 2010-03-25
Don't know what your "merge" plan is, but regardless, do NOT use GParted to touch the Win7 OS partition, period.  IF you attempt to resize it using GParted, you run the risk of corrupting the OS partition and rendering Win7 unbootable.

So, if you're going to resize the Win7 partition to incorporate the unallocated space, use the Win7 Disk Management utility, instead.

---

