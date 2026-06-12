---
title: "How do I Transfer Ubuntu to a new Hard drive?"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by mikey5555 on 2007-12-26
Hello All, 
I want to do something that seems simple:  I want to COPY or TRANSFER my current UBUNTU installation to a new hard drive.  Tis is NOt just a backup, but a complete transfer, and the original hard drive will be used for something else.  Both drives are SATA drives, and are currently both installed into the same PC.  I created partitions for Ubuntu as follows on the new drive:  
     **50GB on /**
     **1GB on /swap**
     **150GB on /usr**

All I want to do is copy the existing Ubuntu installation, in it's entirety, to the new drive, and have it work.   I will then want to re-format the 1st drive, install Windoze to the 1st drive, and end up with a Dual-Boot system:  Win and Ubuntu.  
I realize I will probably have to re-install Grub, after Windoze, in order to make the system Dual-Bootable. 

Can anyone assist with this scenario...??  
Regards...

mikey5555

---

### Post by Pumalite on 2007-12-26
See if any of this fits the bill:

[http://restore.holonyx.com/](http://restore.holonyx.com/)
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)
you could try sbackup - in the repos
DAR
[http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html](http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html)
[http://dar.linux.free.fr/doc/Features.html](http://dar.linux.free.fr/doc/Features.html)

---

