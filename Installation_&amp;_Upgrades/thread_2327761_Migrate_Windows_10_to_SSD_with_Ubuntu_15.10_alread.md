---
title: "Migrate Windows 10 to SSD with Ubuntu 15.10 already installed"
date: 2016-06-14
forum: Installation &amp; Upgrades
---

### Post by Stephen_Patrick_Shellard on 2016-06-14
As indicated in my post title I am attempting to migrate my existing dual boot system to SSD.  I have already succeeded in migrating the Ubuntu installation to a partition [/dev/sda1] which leaves plenty of space on the SSD for Windows 10.  [I have my home folders on a separate drive  /dev/sdb2 - my previous ubuntu installation is on /dev/sdb1]  I have made various attempts to move the Windows installation using Gparted and Clonezilla but have so far failed, and need some assistance.  

The Windows installation is currently on a separate drive /dev/Sdc  and exists on this drive as 3 separate partitions  /dev/sda1-3 .  I resized the installation to ensure a comfortable fit onto the SSD.    Initially I copied and pasted the three partitions to the SSD.  I then disconnected the old Windows 10 drive, updated Grub,  and attempted to boot into the new windows installation.  However I get an error message saying that a device is missing and referring to a .exe file which is corrupt or inaccurate;  however on reconnecting the old drive it boots up fine, but into the old - painfully slow - drive.  

I then attempted to clone the whole drive [using Clonezilla running from DVD] and move this to the SSD, but the outcome was not successful.  I have attempted various other permutations using Clonezilla.   I have also attempted to move the windows installation using the dd command, disconnected the old drive, updated grub, with apparent success, but then a failure to boot into windows, as previously reported. 

I have some experience of using Gparted but no previous experience of using dd, so would classify myself as fairly experienced but very far from an expert in these  matters.  

Help appreciated.

---

### Post by Stephen_Patrick_Shellard on 2016-06-18
I have managed to do this now.  My error was to start by moving Ubuntu onto the SSD.  I started again and this time, using Conezilla cloned the disc with windows onto the new SSD. It was essential at this stage to clone the disk to the SSD disk [rather clone a disk image to the SSD.]  

 I then, using Gparted, resized the Windows partition to make space for my ubuntu installation  which I simply copied and pasted, using Gparted, from its existing location.

I should also mention that it may be necessary to change the UUID number of the source partitions/drive  which will, following the clone, be the same as the target partitions.  Gparted will assign a new UUID number to an unmounted partition, where this is required.

---

