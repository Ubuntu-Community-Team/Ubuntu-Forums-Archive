---
title: "adding a new hard drive size problem"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by gorilly on 2007-09-10
Hi 

ive added a new hard drive to my ubuntu server

i did an fdisk /hdc1/ made a mount gave it a name etc etc...

ive mapped a drive on a windows client, the drive is 160GB but on the windows client its only showing up as 30GB...


here are my settings

> Disk /dev/hda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4892    39294958+  83  Linux
/dev/hda2            4893        4982      722925    5  Extended
/dev/hda5            4893        4982      722893+  82  Linux swap / Solaris

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       19456   156280288+  83  Linux



help please getting it to the correct size!!

thanks

---

### Post by gorilly on 2007-09-11
anyone? im thinking about gparted from the live CD but dont want to because the box has no cd rom is is now hidden away under lots of junk

---

### Post by gorilly on 2007-09-12
thanks for all the help... not

i did it in the end anyway....


sudo mkdir /home/michael/hd2 <this makes a new directory in my home folder called HD2
sudo fdisk /dev/hdc <this makes a new partition on my hdc, options were n (for new partition), 1 (for partition 1) then defaults
sudo man mkfs /dev/hdc1 <this formats the new partition as ext2
sudo mount /dev/hdc1 /home/michael/hd2 <mounts the new partition as the directory we made

i then did a reboot

then logged into SWAT, made a new share, pointed it at the hd2 directory and mapped my network drive.

now i have a 150GB mapped drive...

---

