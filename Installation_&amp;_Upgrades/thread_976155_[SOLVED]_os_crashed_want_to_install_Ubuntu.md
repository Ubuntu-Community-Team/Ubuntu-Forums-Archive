---
title: "[SOLVED] os crashed want to install Ubuntu"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by vamsi Katneni on 2008-11-09
Hi,

i am using Windows XP previously and my os crashed. now i want to install ubuntu without loosing any data from my harddisk .

Please Help!!!

Regards,
vamsi

---

### Post by kanterjoe on 2008-11-09
First, get an install disk. If you can, download and burn it, but it sounds like your computer is kinda pooped so maybe check the library? i heard sometimes you can get them there. 

when you get to the part of the install where you partition the harddrives, resize the partition where you have your data. if all that was installed was XP, you should have either one or two partitions: an NTFS partition that was your C: drive and perhaps a FAT restore partition. what you want to do is resize the NTFS partition. this will turn the unwritten parts of the partition into a new partition, while leaving the written part untouched. 

once this is done, you should have an a smaller NTFS partition and a blank space (and maybe that restore partition). turn the blank space into a EXT3 partition (its the norm for linux, you can choose another file system like XFS or Reiser but EXT3 is default) whose mount point is "/" 

then install the rest of the system. Ubuntu has always recognized NTFS partitions for me, so it should see that there is one and you should be able to get your files once everything is up and running.

---

### Post by vamsi Katneni on 2008-11-10
Did you mean partitioning the C drive from Windows. Actually I'm unable to login to my system? It gives me error which says "NTDetect failed". Now since I can't login I won't be able to Partition the free space available in the hard disk and hence will be unable to install Ubuntu as there are no partitioned drives. Can I partition the hard disk using the Ubuntu Boot CD itself during the installation of Ubuntu?

---

### Post by Ryadt on 2008-11-10
Download the gparted livecd to partition your disk. Then do the install.

---

