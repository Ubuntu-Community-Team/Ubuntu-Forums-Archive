---
title: "Partitioning Problems HELP!!!!"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by Gimpy Turtle on 2007-12-22
I First posted this in Absolute beginner talk but it didn't help, maybe someone in here knows what to do?



"Hey guys,

I am a total noob at the whole Ubuntu thing, but I installed it previously for the animations like compiz fusion etc. The first time I installed Ubuntu I got to the partitioning screen and I had a slider showing how much i wanted to use and I selected 10gig and it installed perfectly fine, but my old graphics card wouldn't handle the animations so I deleted the Ubuntu partition with Paragon Partition Manager and redisrubuted the free space to my Win XP partition. But recently I got a new graphics card which would handle it, so I tried to install Ubuntu again using the same Live CD, but when i got to the partition screen the Guided one now wants to use all of my hard drive, then I went into the manual one and I says i have no partitions, just 40gigs of free space (my HD is 40Gig)

I was wondering if there was anyway to fix the install so the slider came back up or if the manual partition can show my NTFS partition."

(This is what GParted shows even though I know there is an NTFS Partition and Extended Partition)
[http://i156.photobucket.com/albums/t...h/gparted2.png](http://i156.photobucket.com/albums/t...h/gparted2.png)



Someone told me to **sudo fdisk -l** in the terminal of ubuntu and post the results, this may help solve the problem?:

[B]Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c879c87

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3557 28569208+ 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda3 4865 4865 472+ 5 Extended
Partition 3 does not end on cylinder boundary.
[/b]


someone help PLEASE!

---

### Post by Pumalite on 2007-12-22
If you are using Vista, you have to allocate space for Ubuntu with Vista partitioner first.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by Gimpy Turtle on 2007-12-22
I am not running vista, does anyone know how to fix the partition table cause i got reccomended to do that??!?!!?!!?

---

### Post by Pumalite on 2007-12-22
TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by Gimpy Turtle on 2007-12-22
alright i will try that test disk program

---

