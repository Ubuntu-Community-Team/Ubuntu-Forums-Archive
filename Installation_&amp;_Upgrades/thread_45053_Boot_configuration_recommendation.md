---
title: "Boot configuration recommendation"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by kook44 on 2005-06-28
Hi-
My PC is a P3 833 that I would like to install ubuntu on with XP dual-boot.  I tried out the live CD and everything seemed to work great.
I have a 20 gig hard drive that XP is on and an external 100 gig firewire formatted w/ FAT 32 (live CD recognized perfectly) for my data.
I have ordered a 120 gig internal that I would like to put ubuntu on.  I would like to not touch the XP drive at all, if possible.  Im assuming i can put the boot loader on a floppy for when I want to boot ubuntu.  Can anyone recommend the HD configuration I would need to do this (primary/secondary, master/slave, etc...)?

I would like to format the new drive with ext2 or ext3, but I want to share some files occasionally between XP and ubuntu with the external(FAT 32) drive.  Is that possible?

---

### Post by mingus on 2005-06-28
[QUOTE=kook44]I have ordered a 120 gig internal that I would like to put ubuntu on.  I would like to not touch the XP drive at all, if possible.  Im assuming i can put the boot loader on a floppy for when I want to boot ubuntu.  Can anyone recommend the HD configuration I would need to do this (primary/secondary, master/slave, etc...)?

I would like to format the new drive with ext2 or ext3, but I want to share some files occasionally between XP and ubuntu with the external(FAT 32) drive.  Is that possible?[/QUOTE]

This is fairly straightforward, it's just a matter of how you want to do it - with Linux, there are always a lot of choices.  And easy to keep entirely separate from W$.

Re the HD configuration on the controller, the only Linux consideration is your boot strategy.  You indicate using a boot floppy for Ubuntu, and that works very well, and you can easily dual-boot from that floppy into W$.  Or you can do exactly the same thing from the Ubuntu HDD; all that's required is to set this drive as the boot device in the BIOS.  This is a diff decision than where on the channels to put the drive; for performance it's generally best for a HDD to be a master.

With that size drive and somewhat older BIOS, its advisable to use at least 4 partitions.  The 1st is referred to as / (root); 10GB should be plenty.  The 2nd one is for /boot, about 100MB, important that it be at the front of the disc.  The 3rd is for /home which is the equiv of W$ MyDocuments and enables you to manage (e.g., backups) your user files w/o touching the OS.  You can allocate the rest of the drive to /home, but some users prefer to segregate that into more than 1 partition because the nature of the data is very different, e.g., if you do video editing, best to have that separate.  The last is a swap partition (=W$ paging file), 1-2X size of RAM.  It's also a good idea to put /home as a logical in an extended partition, so you can have more partitions later if you want.  Format everything as ext3 except for /boot, make it ext2.

No problem to share the external drive, Linux can read/write FAT32.

Hope that helps.

---

