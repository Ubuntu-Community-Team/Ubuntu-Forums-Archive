---
title: "PATA to SATA Drive"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by dasickis on 2006-11-22
Hey I was wondering how I could take my entire Ubuntu disk image currently on my PATA drive and install it on my SATA drive. 

I need to do this because I need to replace my current PATA drive with the SATA drive and then wipe clean the PATA drive to use as an external drive for my windows laptop.

What would be the best way to do this? I am currently running Ubuntu Dapper. I want to upgrade to Edgy so should I do that before or after?

Thank you,
Praful Mathur

---

### Post by dasickis on 2006-12-16
Maybe my question was a bit unclear, so I'll rephrase it.

I want to swap my IDE Drive with a new Serial ATA Drive so what would be the best way to do that. I am currently running Ubuntu Dapper Drake on an 
--AMD Athlon x64 3200
--400 GB IDE
--500 GB SATA (I'm trying to swap this for the IDE)
--Corsair 1 GB RAM
--NVidia GeForce MX 4000 64MB 

This was my budget PC, but I need to get this swapped ASAP.

---

### Post by bulldog on 2006-12-16
To be honest,if you consider Edgy,I should do a clean install with Edgy from the alternate cd.
So you are sure it works,and copy you data to your new disk if you want.

---

### Post by speedman on 2006-12-16
There are a number of tools like mondo, mkcdrec etc. that you might want to look into.  However, if your IDE drive is on the primary master and your SATA drive is the first such device you could either use dd to copy (block by block) the IDE drive to the SATA drive (which would leave empty space at the end of the drive that you could partition after the fact), or you could partiton and format the SATA drive, copy the system from your IDE drive to it, chroot to the new drive and install grub from there.

For the dd option:

dd if=/dev/hda of=/dev/sda

For the second option:

cfdisk /dev/sda

Create your partitions.

mkfs.ext3 /dev/sdaX

Where X is the partition number on the SATA drive.  Then mount your new partitions.  For example:

mkdir /mnt/sda1

mount -t ext3 /dev/sda1 /mnt/sda1

Then use cp -a to copy your system from the IDE drive to the SATA drive.  Then chroot to your mount point:

cd /mnt/sdaX

chroot /mnt/sdaX

Then edit /boot/grub/menu.1st and point everything at the SATA drive and run grub-install.

HTH


SM

---

### Post by dasickis on 2006-12-18
Hey Thanks I got everything up and running. 

I just decided to install edgy and copy my files over...works perfectly thanks a bunch!

---

