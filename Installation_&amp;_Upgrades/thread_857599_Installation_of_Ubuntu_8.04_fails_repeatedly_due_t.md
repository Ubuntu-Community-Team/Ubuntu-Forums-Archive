---
title: "Installation of Ubuntu 8.04 fails repeatedly due to partition problems"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by NGKEIB on 2008-07-12
Hi all,

I've been trying to install Ubuntu for most of the day, using the official Ubuntu CD.  Don't have Windows, so I just want to put the disc in, and have Ubuntu as my sole OS (no dual-boot etc.).  The normal installation always freezes, so I run it in safe graphics mode, and it works fine up until a point.

I get to the step in the installation process that is about partitioning, and as I'm fairly new to this, I initially selected the guided method, and finished the rest of the steps.  When it tried to partition, it would get to 5% and then I would get this message:

"Failed to create a file system

The ext3 file system creation in partition #1 of SCSI1 (0,0,0)(sda) failed."

I tried again repeatedly, but always with the same result.  Tried to do it manually, and would create a new partition tree (or whatever it's called), create a 20 GB ext3 file system for the /, and also create a 2GB swap one, and leave the rest unfilled, and try to proceed, but I would get the exact same message, also at 5%.  I'm getting a bit frustrated, and would be eternally grateful for any advice.

---

### Post by NGKEIB on 2008-07-12
In case anyone wants any specific info, let me know.
I'm using a Toshiba Satellite A105-S4074, with 512MB RAM and a 120GB HD.

---

### Post by Ognid on 2008-07-16
I am having the same exact problem.  I am using a HP Pavilion DV6000, 64-bit system.  Vista has been removed.  I would like to install Ubuntu ASAP.  Thank you for your time.

---

### Post by Partyboi2 on 2008-07-16
Have you tried using gparted to create the partitions first before running the installer. From the ubuntu live cd go system>admin>partition editor

Edit: You can also download the gparted live cd from [[COLOR=Blue]here[/COLOR]]("http://gparted.sourceforge.net/")

---

### Post by Ognid on 2008-07-16
I have, but there was no hdd.  I am running Yoper on a live CD ATM and I am setting up the partitions as I type.

---

### Post by falcon61102 on 2008-07-16
NGKEIB,

Try running the install again but create a partition in front of your ext3 and in the options click do not use.   Then creat your ext3 partitions after it.  Once you get Ubuntu up and running you can go back and format that partition to whatever you want.  There may be something wrong with the first section of your drive and by skipping a portion of it, you may be able to get around the error and then once you have an OS installed, go back and fix it.

Your partition table would then look something like:

Partition  Type  Mountpoint

/dev/sda1     
/dev/sda2  ext3  /
/dev/sda3  ext3  /home
/dev/sda4  SWAP

---

### Post by wookaru on 2008-08-01
I have been having the exact same problem installing 8.04 on an old Dell Dimension 8300. 

I took the above advice created a small 8MB partition at the beginning of the disk and it worked like a charm! Thanks!

---

