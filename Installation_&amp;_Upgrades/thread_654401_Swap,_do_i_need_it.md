---
title: "Swap, do i need it?"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by hotrod6657 on 2007-12-31
Okay, here's my deal.  I've installed a few different distributions and had the installer for each take care of the partitioning just because i'm not very confident of my ability to do it right.  Here's my question, i now have several swap partitions, sure they're only a few hundred MB's but still, i would like that space...  As i understand it the swap only really acts like ram, or virtual memory, if that's true I do have 2 gigs of ram already, so i doubt i really need the swap but how do i get rid of them?  Can i just delete them with GParted and reallocate the unused space or will that screw up my installs?  

I notice that all of the swaps are under a partition named extended so can that whole thing be gotten rid of without causing me problems?  If i do have to configure something to get rid of them how would i go about doing that?

I apologize if this is a pretty common question and i am very new to Linux but i'm learning.  Thanks in advance!

hotrod

---

### Post by meindian523 on 2007-12-31
2GB of RAM usually doesn't need swap but be safe and keep half-a-gig aside,it will come handy when you want to **really** multi-task.

And since I didn't get exactly how your partitions are setup,please post
```

sudo fdisk -l
``` 

(Lower case L)

---

### Post by jualin on 2007-12-31
I agree with meindian. Keep it just in case, it should not bother too much to have about half a gig reserved.

---

### Post by erfahren on 2007-12-31
yes, you need a swap parition, Ubuntu needs it present.  you really only need about 1GB for it though

you can clean up those extra ones using GParted, whether or not you need an extended partition depends on your current partition table

see partitioning rules here: [http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)

---

### Post by sonofusion82 on 2007-12-31
from my experience recently, kubuntu seems to run pretty fine without swap space. i only have 512MB RAM and i was messing up with /etc/fstab and kinda messed up the entry for swap partition without realizing it. i only found out a few weeks later. I have fixed the swap partition entry in /etc/fstab to reenable it but i have not noticed any problem even when it was disabled. the only thing is that i can't hibernate.

---

### Post by erfahren on 2007-12-31
I always thought it was necessary to have

---

### Post by forestpixie on 2007-12-31
I don't believe that it's necessary as such - unless you need to hibernate, but if you happen to use apps that use a lot of ram it would be helpful to have it

I have 1Gb ram and 1 of swap - the swap very rarely uses more than 40Mb, but I don't think that having a small part of hdd space set aside should cause too much in the way of problems

But you do only need 1 swap partition

---

### Post by hotrod6657 on 2007-12-31
Okay, here's the output of sudo fdsk -l:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12243    92557048+   7  HPFS/NTFS
/dev/sda2           12244       12921     5125680   12  Compaq diagnostics

[B]Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5a85b6a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37590   301941643+   b  W95 FAT32
/dev/sdb2           37591       38197     4875727+  83  Linux
/dev/sdb3           38839       38913      602437+   5  Extended
/dev/sdb4   *       38198       38838     5148832+  83  Linux
/dev/sdb5           38864       38913      401593+  82  Linux swap / Solaris
/dev/sdb6           38839       38863      200749+  82  Linux swap / Solaris[/B]



Obviously the linux partitions are on sdb, the other disk is my internal hard drive that i've kept linux free.

---

### Post by Steveway on 2007-12-31
Also, Live-CD's also use the Swap.
So if you are often trying out distributions then it is pretty usefull.
And of course the obvivious Suspend to Diskn needs Swap.

---

### Post by bharadwaj on 2007-12-31
Ram does'nt support you 100% without a good swap partition

---

### Post by meindian523 on 2007-12-31
Um,could you cite some sources for that remark?

---

