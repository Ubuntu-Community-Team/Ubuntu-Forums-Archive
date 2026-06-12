---
title: "Hard drive not being recognized"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by Jefft on 2007-05-12
I'm brand new to ubuntu and I am having trouble seeing one of my hard drives.  It is a WD SATA 500GB full of  files that I used just as storage on my previous windows installation and it is in NTFS format.  It does not seem to be recognized by ubuntu.  The strange thing is that it was recognized and could be accessed when I run ubuntu directly from the CD, also I have another SATA drive in my machine that IS being recognized and runs fine so I don't think its an issue of SATA drivers.  Is there any way to access the drive without re-formatting?  Please someone help me, and remember I am brand new to Linux so I'm very unfamiliar with the Linux jargon.:-s

---

### Post by Psicolonia on 2007-05-12
first make sure you didn't hibernate windows with the drive on. if you are using ntfs-3g that wont work.

afterwards try to mount it manually.

mkdir externalSATA
sudo mount -t ntfs /dev/sda1 externalSATA

replace sda1 with your device name. this will be compatible. as root, try to list the externalSATA directory, if you can see the contents of the drive you just have to add reference to it to /etc/fstab

that will at least tell you if the drive is being recognized.

---

### Post by Jefft on 2007-05-12
Thanks for your help, I tried using /dev/sdc1, sdc, sdd, etc.. (sda1 and sdb2 are already being used by my two other drives)  but it said the device "does not exist."  I also tried fdisk but it does not show up on there either.  Can anyone guess why it would recognize it running with the live cd, but not in the installed version? Does the drive size (500GB) matter?

---

