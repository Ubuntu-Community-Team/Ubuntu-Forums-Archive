---
title: "Weird problem while partitioning."
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by Runek1ller1 on 2010-06-07
Hi, I downloaded the AMD64 installer for the latest Ubuntu (10.04?), and I have made it bootable on the hard disk through unetbin. I have managed to get the installer up and everything goes very well up until the partitioning part. 

The installer tells me that my installation medium is on /dev/sda2 and I cannot change this option and various other things. I have created 50gb of free space as shown in the images and have even tried with 2 different versions of Ubuntu, 8.10 (32bit) and 9.04 (32bit) and have encountered similar problems. :mad:

I would love it if anyone has anything which could help me to try and resolve this as I would like to keep Ubuntu. 

Extra info: partition sda2 contains Windows 7 64bit.

---

### Post by oldfred on 2010-06-07
It is normal that gparted will not work on a mounted partition. Usually you install from a CD or USB key to make sure nothing is mounted. But I would expect you to be able to install into the free space.

Have you tried manual install where you have to create the partitions. You need 10-20GB for / (root) 2GB or RAM size (if you want to hibernate  for swap and the rest for /home. Then with the installer you choose those partitions for the install.

---

### Post by Runek1ller1 on 2010-06-07
Can you please guide me through how to do a manual installation, if it is possible on unetbin? I don't understand why the other versions would not install and they came out with similar problems (can only choose to use the whole disk for Ubuntu) and they were both on CD, I have no clue to why I can't install on the free space, according to the installation I can only install on sda2, but that's my Windows partition. 

There's no other options to install to the free space and if I click forward it still gives an error (something about root file system) I'm totally baffled and i've tried nearly everything to try sort it out :(

---

### Post by oldfred on 2010-06-07
Then did you download the wubi version that is intended to install into the NTFS windows partition?

---

