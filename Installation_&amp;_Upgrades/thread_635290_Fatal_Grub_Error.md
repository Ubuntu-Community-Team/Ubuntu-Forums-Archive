---
title: "Fatal Grub Error"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by System Monitor on 2007-12-08
I get this is the error everytime i try to install ubuntu 7.10
Executing 'grub-install (hd0)' failed.
This is a fatal error

---

### Post by jimbob on 2007-12-08
That suggests there may be something wrong with the boot sector on your hard drive.
If you are not using the alternate CD try it - you may get some additional information.

Also if you have a stand-alone recovery disk you can try grub-install from a terminal command line and see what happens.

---

### Post by Pumalite on 2007-12-08
If this is a laptop, Grub might be trying to install to a hidden recovery partition at the front of the drive. If not, you can try rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
to investigate your drive, or TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download) to repair it if necessary. OTOH, all you might need is the Alternate CD as the prior poster said.

---

### Post by System Monitor on 2007-12-08
no it is not a laptop

---

### Post by pietjanjaap on 2007-12-08
hd0, try to change it to different settings, like 0,1  0,1  1,0 1,1  if you have more harddisks.

if you think grub is not working at all, try to install grub with supergrub, this is a bootable cd to install grub.

---

### Post by System Monitor on 2007-12-08
i have the cd, but what do i do then

---

### Post by Pumalite on 2007-12-08
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk)

---

