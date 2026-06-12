---
title: "Still can't install!"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by CoriolisSTORM on 2007-08-19
Alright ladies and gentlemen, I'm still at it with trying to install Ubuntu LTS onto my PC.  I have done an MD5 sum check on the ISO and then I verified everything on the CD.  It boots fine, but when I get to the point where it starts to resize one of my partitions, it gives me an error, "Unable to create enough free space."  Last time I tried GParted as well, and it did not like it, Partition Magic also gives me an error when I try to repartition it.  Is there some way I can actually install it or do I need to give up?  I have 58 GBs free and 47 used.  total is 110, HP took some of the 120 for my recovery partition (cant delete it, their CD creator program will not work right to give me some backups.)  So, what do I need to do?

---

### Post by Pumalite on 2007-08-19
Post specs. What OS do you have now?. Laptop or Desktop?

---

### Post by wolfen69 on 2007-08-19
you should probably run the manufacturers  hard drive diagnostics tool.

---

### Post by Pumalite on 2007-08-19
HP took some of the 120 for my recovery partition (cant delete it, their CD creator program will not work right to give me some backups.) So, what do I need to do?
__________________
To correct this you could use DBan: [http://dban.sourceforge.net/](http://dban.sourceforge.net/) Then get an OEM CD for ten bucks. You can use your serial number stuck in the computer.

---

### Post by CoriolisSTORM on 2007-08-19
Sorry, I was in a bit of a hurry, had to meet a friend somewheres.  Anyway, its an HP Pavilion A320N, desktop.  AMD Athlon XP 2800+ Barton, Asus A7N8X-LA, 512 MB RAM, 120 GB HDD, Nvidia Geforce 4 MX integrated (takes 64 MB of my RAM)  OS currently installed is XP Home, and I have a 5.5 GB recovery partition from HP on it as well.  Who offers a hard drive diagnostic tool?  I cant remember what type of drive is actually in here, I want to say Samsung?  :confused:
edit:  Pumalite, as far as what to do, I dont really know, I'm just hoping my HDD never dies.  
edit again:  File system is NTFS on the C:\ Partition, I the D one is FAT32.

---

### Post by Pumalite on 2007-08-19
If you want to keep XP and the recovery partition use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

I personally would get rid of windblows and use the entire disk for Ubuntu, but that's me.

---

### Post by CoriolisSTORM on 2007-08-19
I've tried Gparted the last time I ran this (or tried to) and it didn't work then either, but maybe it'll give me a specific error message, I'll try it and give you the error, maybe then it will help in tracking down the problem.

---

### Post by Pumalite on 2007-08-19
Stick a Live CD in there, mount your drive and post: fdisk -l (small L)
If Ubuntu does not boot, try Knoppix: [http://www.knoppix.org/](http://www.knoppix.org/)

---

### Post by CoriolisSTORM on 2007-08-20
Ubuntu boots quite well, I just cant get the installer to work.  here is what 
```
sudo fdisk -l
``` gives me.

> Disk /dev/hda: 120.0 GB, 120060444672 bytes
240 heads, 63 sectors/track, 15508 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         771     5828728+   b  W95 FAT32
/dev/hda2   *         772       15508   111411720    7  HPFS/NTFS


---

### Post by Pumalite on 2007-08-20
Well, you have XP OK, but need to make partition for Ubuntu and install. I'm afraid that the recovery partition is the problem and unless you delete it and make new partition, nothing will work. On the other hand, read documentation for Gparted carefully so you know how to use it. Gparted should be able to shrink your XP partition. It helps to defrag XP several times and erase all temp files before shrinking partition. Also use Gparted, the stand alone, burn to CD, bootable program. It's newer, more advanced and more flexible than the one that comes with the installer. At the end you might have to make achoice between XP and Ubuntu, but is not that way in most cases.

---

### Post by CoriolisSTORM on 2007-08-20
Its very odd, I've had Ubuntu on here in the past, but deleted it and its partition.  Now it won't let me install it again.  I'll do several defraggs and try gparted (the Live CD, got it somewhere here) again.

---

### Post by merlinus on 2007-08-20
Is it not amazing what these OEMs do to keep from providing paid-for OS disks!

From what I can see from sudo fdisk -l, and the OP saying that c drive is NTFS, it would seem that the partitions and drive letters have been switched around by HP.

hda2 is NTFS, and the second partition on the hdd, yet it is drive c.

So I would agree with Pumalite, in that unless the rescue partition (hda1) is deleted, no install of ubuntu will be straightforward.

OTOH, gparted live cd often can work wonders.

-merlin

---

### Post by Stan_1936 on 2007-08-20
Regarding GParted, I find that with no operating system installed, it sometimes gives trouble.  For me it would not load from its Live-CD even with forcing the VESA driver.  However, Parted Magic(or Partition MAgic) works with the driver of your graphic card even with a totally empty disk.

cdisk was a bit tricky at the beginning.  Parted MAgic helped clear up a lot, maybe it's the graphical interface.

---

### Post by CoriolisSTORM on 2007-08-20
Gparted Live CD was a no go either.  Here's the info it gathered followed by the error.  I clicked on information due to an exclamation point being next to my C drive.  

> 
Filesystem:  ntfs
Size: 106.25 GiB
Flags:  boot

Path: /dev/hda2
Status: Not mounted
First Sector 11657520
Last Sector:  234480959
Total Sectors:  222823440

Warning:
ntfs resize v1.13.1.1 (libntfs 9:0:0)
Device name: /dev/hda2
NTFS volume version: 3.1
Clustersize: 4096 bytes
Current volume size: 114085597696 bytes (114086 MB)
Current device size: 114085601280 bytes (114086 MB)
Checking filesystem consistency...
Accounting clusters...
Cluster accounting failed at 4660991 (0x47{dunno if I wrote L or 1)eff):missing cluster in $Bitmap
Cluster accounting failed at 13926464 (0xd48040): extra cluster in $Bitmap.
filesystem check failed!  Totally 2 cluster accounting mismatches.  
ERROR:  NTFS is inconsistent

It then tells me to quit to windows and run checkdisk and then reboot twice.  I have done this before to no avail, this is as far as I got last time I tried to install.

---

### Post by merlinus on 2007-08-20
Did you run chkdsk with the /f switch?  Run it on both c and d.

-merlin

---

### Post by AcworthJack on 2007-08-20
If you have 2 Gig free in your windows partition you could install Wubi Ubuntu [http://wubi-installer.org/](http://wubi-installer.org/).

If you still wanted "real" Ubuntu - you might have beet success creating the parition once Wubi Ubunut was up and running.

Good luck,
John

---

