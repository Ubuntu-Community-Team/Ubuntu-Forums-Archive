---
title: "GRUB Hard Disk error"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by VenisonMogambi on 2008-09-08
Hi,

A couple months ago I installed Hardy Heron 8.0.4.1 on my 160 GB primary master HD, then  moved my /home directory to my 80 GB primary slave HD. Everything was fine, then out of the blue, I booted the PC one day and got this error message: GRUB Hard Disk Error.
I had previously been dual-booting Windows XP and Linux, and when I wiped both hard drives and went all Linux, I kept the same GRUB, so I suspect I might have to re-install GRUB, something like that?
When I boot from a Hardy Heron CD and do a sudo fdisk -l I get the following:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225289 byets
Disk identifier: 0x7b9fbb67

  Device Boot      Start      End   Blocks    Id  System
/dev/sda1              1     9729  78148161   83  Linux

So does that mean it's trying to boot from my 80 GB slave drive, where I kept my /home directory, while the Linux OS itself is on the 160 GB master?

---

### Post by Rocket2DMn on 2008-09-08
That's not good if it can only see one hard drive.  Try disconnecting the slave drive, setting the jumper on the primary hard drive to either Master or Cable Select, then booting from the LiveCD again and checking fdisk.  If that fails, try a different cable and/or IDE port on the motherboard.  If it's still not detected, I would have to say your hard drive is dead.  A last ditch effort could be to plug the drive into an external case and try to access it with USB.

---

### Post by VenisonMogambi on 2008-09-08
> **Rocket2DMn said:**
> That's not good if it can only see one hard drive.  Try disconnecting the slave drive, setting the jumper on the primary hard drive to either Master or Cable Select, then booting from the LiveCD again and checking fdisk.  If that fails, try a different cable and/or IDE port on the motherboard.  If it's still not detected, I would have to say your hard drive is dead.  A last ditch effort could be to plug the drive into an external case and try to access it with USB.


I think you're right - I think the hard drive is dead. I disconnected the 80 GB drive and just connected the 160 GB drive as master. The BIOS gave an error message about Boot Disk failure, and when I used the Ubuntu CD and did an fdisk, it returned nothing.
Now...since I moved my /home to a seperate partition on the 80 GB drive, and GRUB recognized and tried to boot from that drive (so I assume that drive still works okay), I should be able to re-partition that drive, load Ubuntu on the new partition and save my /home directory, right?

---

### Post by Rocket2DMn on 2008-09-08
Yes.  First, I would backup that other hard drive to an external disc if possible - you don't want to risk losing that data should the partitioning fail.  What you will have to do is repartition the drive to make room for / and swap - I would create the partitions in advance.  Then when you go to install Ubuntu you will need to use custom partitioning (I'm not sure if the LiveCD can do this, I hope it can, otherwise you need the alternate install cd - let me know).  Tell it which partition to use for root, which for swap, and which for /home - be sure to NOT reformat the /home partition.
Then your install should proceed normally and you will have a fresh Ubuntu with your old /home partition.  You will have to re-install all your programs, but the configs will already be in place.

---

### Post by VenisonMogambi on 2008-09-12
Well, I went ahead a re-loaded Ubuntu on to my remaining drive. The install went fine, and there's a partition manager at the beginning of the install process that allowed me to carve out a partition on which I put the new Ubuntu install. I wasn't sure if my original /home partition would survive, but sure enough it's there on my Desktop, under "Places" as a 43 GB drive. I'm very confused, though. When I do a fdisk -l, I get the following output:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b9fbb67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5287    42467796   83  Linux
/dev/sda2            5288        9729    35680365    5  Extended
/dev/sda5            5288        7719    19535008+  83  Linux
/dev/sda6            9542        9729     1510078+  82  Linux swap / Solaris
/dev/sda7            7720        9459    13976518+  83  Linux
/dev/sda8            9460        9541      658633+  82  Linux swap / Solaris

How did I end up with 8 partitions? Ultimately, I'd like to have my /home drive back on its own partition and just have the two partitions: the Ubuntu and my /home directory? If you can help me figure this out I'd appreciate it.

---

### Post by Rocket2DMn on 2008-09-12
Actually there are 6 "partitions", 1 of them is an extended partition, so there are really only 5.  It's really impossible to tell why you have so many still, since you said you just created new partitions and did an install.  Can you please post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```

---

