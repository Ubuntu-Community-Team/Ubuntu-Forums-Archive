---
title: "How does ubuntu decide where to choose boot partition and install grub?"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by bdalzell on 2006-08-22
I have a dual boot system with Ubuntu and another isolinux launched system called Amithlon. Originally I only had Amithlon and it had grub in a fat partition hda1. When I installed Ubuntu it choose to install its own grub and make the root Ubuntu partition hda11 (a lot of partitions are used by the other OS) into the boot partition. So i just edited the grub menu.lst that it installed and went on from there. However last night I decided I wanted to experience the minimalist joys of Xubuntu and I had a unused partion hda2 and tried to install Xubuntu. When I tried the manually choose to partition part of the installation gparted kept crashing but when I decided to give up on the Xubuntu installation I found that the system generated a Grub 22 error and was not bootable. My attempts to edit grub during boot to point it to the old Ubuntu boot partition did not work, however both the alternate OS and Ubuntu would boot from their respective live CD's and I could mount the partitions and verify that all the data was there.

Eventually I went a head and let Xubuntu install itself. What it did was to resize by Ubuntu partition, not recognize and reuse the swap partition and make two new partitions (one a new swap) and install itself to boot on hda12 (new). As part of my fooling around I had tried deleting a parition (hda7) hoping xubuntu would use it but all that happened was that higher partitions got renumbered. 

The final result of all this is that I edited the grub menu.lst on hda12 so that the alternate OS, Ubuntu and Xubuntu are all bootable. But I would really like to have the computer keep grub and the bootable kernels in hda2 and be able to boot from there. Hda2 is currently an empty Ext2 partition - I had a  previous Linux in it which Ubuntu ignored when I initially installed Ubuntu.

Is there a simple way to do this? During the fooling around stage with Xubuntu I tried copying grub and the kernels to hda2 which I set as bootable with gparted but I just kept getting a grub 15 error early in grub booting which did not get far enough to display the contents of menu.lst.

---

