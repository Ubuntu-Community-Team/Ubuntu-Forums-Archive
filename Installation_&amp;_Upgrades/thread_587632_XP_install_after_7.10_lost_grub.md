---
title: "XP install after 7.10 lost grub"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by chlhardy on 2007-10-22
Howdy,

Here's my set up:

3 partitions
  - One XP Pro
  - One Gutsy Gibbon
  - One data

Originally I installed XP, then GG so GRUB took control of booting and all was good.  Then like Windows users have to do, i had to reinstall and of course MBR took control.  And since MBR is deaf, dumb and blind, it doesn't see the linux partition. 

So...I booted with the Live CD and tried to reinstall GRUB but it couldn't mout the partition when I tried the setup command.  When I go to 'Computer' it sees the partitions but partition manager shows one giant unallocated drive.  I even tried reinstalling GG but when I went into the manual settings for installing on certain partitions, it only showed one partion.  

I know i can probably set MBR to see Linux but GRUB is a lot pretty and better, i'm sure.

Oddly enough, when i originally installed GG with XP already on it, it saw all three partitions just fine.

BTW: I have a Dell Inspiron 6000 with a SCSI drive.

Any ideas?

Thanks

---

### Post by dagrump on 2007-10-22
If the partition tool only shows 1 partition, windows most likely wiped & took the whole drive. If you could get a copy of gparted live disk (sorceforge) you could verify if that is the case. Anyway it's a handy tool to have.

---

### Post by chlhardy on 2007-10-23
Nah, i'm looking at windows disk manager and it sees all the partitions including my linux and swap ones.  I'll see what gparted finds out and i'm gonna try to get Kubuntu installed....sorry David.



P.S. That was a shout out to David the Gnome in case you were wondering.

---

### Post by chlhardy on 2007-10-23
So...Gparted or the Kubuntu 7.1 live CD parttion manager cant see the partitions.  Although when I open up 'computer' i can see them just fine.

I also tried installing off the kubuntu live cd and it also couldn't see the partitions, just a single unallocated space.

Anyone goy any ideas? I really dont want to have to start from scratch.

Thanks

---

### Post by chlhardy on 2007-10-24
So the issue is solved for the most part.  I was able to fix Grub with the Super Grub disk but I linux partition manager still cant see any partitions.  This means I cant upgrade or reinstall without redoing the whole computer.

Any ideas on how to make it see the partition table.

---

### Post by meierfra on 2007-10-24
What is  the output of

```
sudo fdisk -l
```

 If your partition table is screwed up,[ testdisk  ]("http://www.users.bigpond.net.au/hermanzone/p21.html")  might be able to   fix it.

---

### Post by chlhardy on 2007-10-25
The outpu to of fdisk -l is:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce31ce31

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        9728    52540582+   f  W95 Ext'd (LBA)
/dev/sda3            5100        9728    37182411    7  HPFS/NTFS
/dev/sda5            3188        4524    10739389+  83  Linux
/dev/sda6            4525        5099     4618656   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS


So it can see everything ok and grub works fine.  Unfortunately, gparted or the live cd cant see any partitions at all.

---

### Post by chlhardy on 2007-11-05
So i finally blew away the linux partitions in disk management, formatted them in NTFS and installed Kubuntu on them

Issue solved.

---

