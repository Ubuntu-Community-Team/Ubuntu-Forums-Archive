---
title: "partition disk"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by Crim_son on 2008-04-12
Hey guys probably something simple but if you could help I sure would appreciate it.  My first time running the installer on the ubuntu 7.10 everything worked great got to partition part of the installation and I selected Guided - resize the partition and use the freed space as my option I didn't adjust the slider or anything just thinking it was already preset to the right setting.  Well it errored on me and now when I try to do the partition option there are only 2 options "Guided - use entire disk" and manual...I need to know how I can get back the freed space option please.  Thanks guys.

---

### Post by Pumalite on 2008-04-12
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to doisk and boot from it. Right click on XP (if you are using Vista, you have to use the Vista partitioner) and choose 'resize' from the menu. In the fre space, you can make 3 'New' partitions:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for home. Install Ubuntu, go 'Manual' and choose the partitions already prepared.

---

### Post by twist2b on 2008-04-12
Actually, Gusty and Hardy come with a partition editor under system>admin
You can edit the partition before installing the system.

Or during the install there is a partition editor, Though thats all obsolete in the alternate CD

you can edit your disk with XP or Vista aswell by right clicking "computer" and selecting "manage"

---

### Post by Pumalite on 2008-04-12
it's better to partition an unmounted drive.

---

