---
title: "Grub, Error 22 Help Please"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by DerangedDingo on 2007-05-24
Hi,


My question is, from the LiveCD, would 'grub-install' be "clean" or should I burn super-grub disk to a CD and do fix /mbr or however that goes if I get Grub Error 22

Full Story (doesn't really matter): 
I've been using Edgy for a while, and I decided to upgrade to Feisty after I received a LiveCD from my friend. I booted up, and repartitioned my drive like this:
(I took each step one at a time to prevent data loss)
I copied my Dell Recovery Utility partition over to a partition on my flash drive
Deleted the Dell Partition so I would only have 3 primary partitions on the drive
Resized the NTFS partition so I would have a total of 12 gigs on ext3 (I only had 6)
Made a 6.5 gig ext3 partition in that space.
Copied my ext3 partition to the new one
(At this point, I finished, made one new line in my /boot/grub/menu.lst for the new partition, and booted it to see if everything had gone smoothly.)(Then I booted back to the LiveCD to continue)
I deleted my original ext3 partition and enlarged the new one appropriately, as well as removed the line in the grub menu.lst

So, basically, hd0,2 was STILL hd0,2, nothing had been moved, the only difference was the ext3 partition was twice its size and hd0,0, the dell partition, was now unallocated space... But, I restarted and, voila!, Grub Error 22.

---

### Post by confused57 on 2007-05-24
I believe if it were my system, I would do a fixmbr just to see if Windows will still boot OK.  You can always reinstall grub using the live cd:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

You might want to open a terminal in the live cd & see what the results are of:
```
sudo fdisk -l
```
you probably already know, but the -l is a lowercase "L"

Your partition filesystem UUID's have probably changed, so you might want to run:
```
blkid
```

Then mount your root partition & compare the UUID's with what's in your /etc/fstab and the kernel root UUID in your menu.lst.

Here's how to mount ext3 partitions:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

You could probably mount your partition, run blkid, then just copy & paste if the UUID has changed.

Since your former (hd0,0) is unallocated, your root partition "might" be (hd0,1), I'm not sure.

---

### Post by DerangedDingo on 2007-05-24
grub> geometry (hd0) returns
[PHP]drive 0x80: C/H/S = 4863/255/63, The number of sectors = 78125000, /dev/sda
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type unknown, partition type 0x7
   Partition num: 3,  Filesystem type unknown, partition type 0x82[/PHP]

Filesystems Unknown?

sudo fdisk -lu returns
[PHP]ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1        50444100    76453334    13004617+  83  Linux
/dev/sda2           64260    50444099    25189920    7  HPFS/NTFS
/dev/sda4        76453335    78027704      787185   82  Linux swap / Solaris

Partition table entries are not in disk order
[/PHP]

and finally, blkid returns
[PHP]/dev/sda1: UUID="396cf85d-e2ea-400d-9607-884e5c22f891" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: TYPE="ntfs" 
/dev/sda4: UUID="118b8a56-2d01-4310-96be-bc84b0f9dc50" TYPE="swap" 
[/PHP]

Does this mean that my hd0,0 partition is linux?
Further evidence:[PHP] grub> find /boot/grub/menu.lst
 (hd0,0)
[/PHP]

Looks to me like some simple naming problems, or something of the sort. I'm going to edit my menu.lst and see if it works.

EDIT: I installed grub to hd0
Time to restart. Thanks for the help! (though I'm not sure if it works yet)

---

### Post by DerangedDingo on 2007-05-24
(5 minutes later) Yes, it works! GRUB at least... because of the different naming I'm not sure what hd0,0 or hd0,1 or 2 or 3 etc, etc are, so.. I can't boot any OS's
So, at the moment, it's just a problem with the menu.lst. It found my splash screen... which, and since that links to hd0,0... I think that one is linux, and hd0,2 is Windows.... not entirely sure though.. I'll hafta mess with it a little.
Thank you for preventing many, many headaches!

---

