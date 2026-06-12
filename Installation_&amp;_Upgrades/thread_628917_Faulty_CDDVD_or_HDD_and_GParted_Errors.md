---
title: "Faulty CD/DVD or HDD? and GParted Errors"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by thisisurlife on 2007-12-01
Ok, so here's the thing

I'm have:
-AMD Sempron 2200+ Processor
-2GB of RAM
-A 40GB HDD with Windows XP installed, Jumper setting as Master
-A 10GB HDD trying to instal Ubuntu 7.10 on, Jumper set to Slave.

Initially my uncle provided me with the Ubuntu Live CD. I booted off the CD, and ran the GParted program to partition my 40GB HDD, for Dual-Boot. Once i resized the HDD, i hit the "Apply Changes" button to make it final. Unfortunately no progress was made and an error popped up. I have forgotten precisely this error said, but essentially it told me that i wasn't able to complete the partition resize. I thought of Dual-Booting off 2 separate HDD's. I have tried this yet it still isn't working, I, again, booted from CD, and clicked the desktop "Install" button, went throught the set-up normally, and chose my Slave HDD as the partition to Install, I begin the installation, and around 27% it pops up with another error, saying that either my CD/DVD is faulty or my HDD is faulty.

Have i done anything specifically wrong? That primarily is what i need to know. Either way, i need to know what i can do to fix this.

Once i get my Ubuntu installed on my Slave HDD, i also need to know how i can configure my system to give me a choice of OS to run (Ubuntu 7.10 or Windows XP)

---

### Post by logos34 on 2007-12-01
Go back and defrag xp disk a couple of time.  You might even have to temprarily disable the paging file/virtual memory, hibernation and/or turn down system restore.  There might be files at the end of the disk preventing ubuntu installer from shrinking it.

Is this a shipit CD or did your uncle download an burn it?  If the latter, verify the md5sum sum and run the check CD for defects if you haven't already.  (could also be a bad burn--needs to be done slowly--i.e. like 4x speed for best results, although I routinely do mine on cd-rw at 10x without problems).  

If you use the 10 GB disk, use gparted to delete all partitions and reinstall using guided option--give it the whole disk.

---

