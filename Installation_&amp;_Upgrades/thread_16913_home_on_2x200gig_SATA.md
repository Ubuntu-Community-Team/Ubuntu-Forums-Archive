---
title: "/home on 2x200gig SATA"
date: 2005-02-24
forum: Installation &amp; Upgrades
---

### Post by deBaas on 2005-02-24
Hello,
I've tryed to install ubuntu serval times without succes. I hope you could help me.
Ubuntu is installed on /hda (a IDE disk), swap partition on over there too.

Due the limited space in /hda I would like to have my /home on anther disk(s).
While installing ubuntu I assigned my two 200 gig both as a LVM partition. I did create a volumegroup "satadisks"  containing both 200 gig SATA disks. 
Then I created a logical volume "data" of 400 gig inside "satadisks". and mounted it as /home with an ext3 filesystem. No problem so far. Basic installation is finised but while rebooting i get:

** Checking all filesystems...
fsch.ext3: No such file or file or directory while trying to open /dev/mapper/sataschijfjes-data

/dev/mapper/sataschijfjes-data:
The superblock could not be read or does not describe a correct ext2 filesystem. 

I also tried to install with the ext2 filesystem wich caused the some problems. Trying software raid0 on these two disks also gave me nothing but trouble. I realy could use soem help.

---

### Post by alastair on 2005-02-24
I won't/can't help with LVM etc. because I have never used it.

But what you could do is just :

a) normal install - everything to first disk
b) once installed, move and link your home dir to the 2nd disk

---

