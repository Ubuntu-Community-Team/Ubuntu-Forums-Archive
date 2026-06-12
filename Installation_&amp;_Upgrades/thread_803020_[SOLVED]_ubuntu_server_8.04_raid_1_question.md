---
title: "[SOLVED] ubuntu server 8.04 raid 1 question"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by cmsimike on 2008-05-21
Hello All.

I am trying to set up an Ubuntu Server install using Raid 1 with two 160 gig hard drives. This is how I am proceeding:

1) For each hard drive, create a primary partition and mark it as a raid partition. 
2) Configure software raid -> Create MD device -> Raid 1 -> pick both hard drives
3) Back at the partitioner, select the newly created raid partition and (FREE SPACE) and click on Automatically partition the free space
problem: Failed to partition the selected disk

This probably happened because there are too many (primary) partitions in the partition table

Now this happens regardless of if I auto partition the raid or if I configure it manually. I create the first 120 gigs as a partition (ext3) which then marks the second part of the raid (the unused part) UNUSEABLE (which I am trying to make swap)
This also happens regardless if I create the raid partitions as primary or logical. Now I am curious what I am doing wrong here.
Please help!

thanks

---

### Post by cmsimike on 2008-05-22
I hate to do this, but I am still desperately seeking any advice in what I am doing wrong.

---

### Post by smithfarm on 2008-06-01
> **cmsimike said:**
> I hate to do this, but I am still desperately seeking any advice in what I am doing wrong.

Right off the bat, I would say you need to partition manually. You see, GRUB won't boot off a huge (multi-gig) partition. You have to put /boot on a small (256-512MB) partition at the beginning of the disk. Put root on a partition that takes up all but about 2% of the rest of the disk. Leave the remaining 2% as free space (just in case you need to replace a failed disk with one that is the same size but not necessarily identical). /boot can be a separate RAID1 device (say md1) and / will be md2. Set up LVM on md2 and leave /boot as it is. Since RAID will mirror /boot on both drives, you can boot the system from either drive.

Hope this helps.  I haven't actually installed Hardy to my RAID system yet, since I found out that the regular Hardy CD doesn't have RAID as an install option. Have to get Hardy Server CD for that, I guess.

---

### Post by ger_macaco on 2008-06-28
I am trying to do the same, a RAID1 with two 250GB SATA disks.

I'm setting up 3 RAID1 devices: md0 (512MB, ext3, /boot), md1 (228GB, ext3, /), md2 (20 GB, swap).

However, Ubuntu Server won't boot. It stays with a black screen and something similar to a cursor on the top left cornet.

What should I do to make it work?

Many Thanks!

---

### Post by punkybouy on 2008-06-28
Just speculation on my part but try not preparing the second drive.  I believe the mirroring process will prepare the mirror.  Right now it sees the partition you created  on the second drive and can't or won't write.

---

### Post by ger_macaco on 2008-06-28
To create de RAID1 devices, I have to create the partitions on both disks and then associate them when creating de md (RAID device) if I don't create the partitions on the second disk, I won't be able to mirror anything

---

### Post by szandor on 2008-08-01
you do not need to create a boot partition for raid 1. just create 2 primary partitions on both drives and make them raid volumes, not / or swap. i.e, for 2 100 gb drives you would have:

drive 0: 
98gb raid (primary partition) (start of disk) (mark bootable)
2gb raid (primary partition)

drive 1:
98gb raid (primary partition) (start of disk) (mark bootable)
2gb raid (primary partition)

now you should have the option to configure the raid 1/create disks. you should have:

sda1
sda2
sdb1
sdb2

group sda1, sdb1 for md0 (/)

save, then create

group sda2, sdb2 for md1 (/swap)

now you should have 2 raid partitions

raid device 0
98gb free
raid device 1
2gb free

select the 98gb, create partition, select filesystem, done. do the same with the 2gb for /swap.

that's it.

grub can boot from raid 1. this is what i had to go through to get my laptop going. when i switched to raid 0, you do the same thing but have 3 partitions on each drive, with /boot at the beginning as a primary partition outside of the raid.

---

