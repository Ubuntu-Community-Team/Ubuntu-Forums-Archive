---
title: "reconfiguring ubuntu alongside windows"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by element6665 on 2012-11-05
Hey guys,
Long time Ubuntu user but not power user by any means. I bought my PC with windows and since formatted my entire drive for my Ubuntu install. However, I now need windows again for work and would like to install Ubuntu alongside windows. I created a recovery disc for my windows install before wiping and going with Ubuntu when I bought my laptop. Im familiar with the pretty painless process of installing ubuntu alongside windows and am hoping I can achieve that. I formatted my drive to NTFS and popped in the recovery disc I have, however, the recovery disc is not able to find any os versions (obviously because I wiped the drive) and therefore it won't allow me to proceed with a restore. I wanted to ask here hoping that someone who uses the 2 os' side by side might have some knowledge on whether or not this is achievable again through a recovery disc or if I would need to buy a full install disc. 

I can load my hard drive and view partitions through a live gparted utility so I know the HDD isn't fried. Any suggestions would be much appreciated. 

Thank you

---

### Post by 2F4U on 2012-11-06
Your problem has not much to do with installing Windows and Ubuntu in a dual boot configuration. It is simply a problem that your hardware vendor did not provide you with a full installation medium. If I were you, I would contact the hardware vendor and ask him how to restore Windows.

---

### Post by carl4926 on 2012-11-06
Probably best to buy win7, because XP is sailing away.
Forget win8 it's a pile of slit

---

### Post by element6665 on 2012-11-06
> **2F4U said:**
> Your problem has not much to do with installing Windows and Ubuntu in a dual boot configuration. It is simply a problem that your hardware vendor did not provide you with a full installation medium. If I were you, I would contact the hardware vendor and ask him how to restore Windows.

Figured it had to do with the disc being recovery only. Thanks for the response, I appreciate the help.

---

### Post by oldfred on 2012-11-06
Most recovery disks are just an image of hard drive, so they need to see the original NTFS partition and its original size. Often better to make a full backup of Windows after shrinking it.

You may be able to fully backup Ubuntu, erase Ubuntu partitions and create the original NTFS partition with the boot flag. Not sure about separate 100MB boot that Windows 7 has or vendor recovery. Some recovery are just CDs that have to have Vendor recovery partition to restore system.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

