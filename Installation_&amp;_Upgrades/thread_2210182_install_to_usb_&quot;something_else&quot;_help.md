---
title: "install to usb &quot;something else&quot; help"
date: 2014-03-09
forum: Installation &amp; Upgrades
---

### Post by GeorgeBerz on 2014-03-09
I made a pendrive ubuntu install and booted form live pendrive installation, im trying to do a full install from that to another usb stick and it looks like I have to do the "something else" option and I dont know what to put...

I want to do a full install on a 8 gig stick what parameters do I need to use re format, partition, fat or ext etc... can someone walk me through the steps, thank you

George

---

### Post by oldfred on 2014-03-09
With 8GB you do not have a lot of room, but I have one 16GB emergency boot full install with 8GB for / and the other 8GB is just for data. You may have to regualarly houseclean kernels & log files. It will not last a long time and will be a bit slower booting and writing. You do need to make some settings to reduce writes.

For BIOS install I would just make / (root), ext4 for entire drive if you have a fair amount of RAM or over 2GB. If not then you may need some swap. 
If UEFI post back as that will be different.

This is older but install process is similar.
 Installs to 4GB flash, newer of Ubuntu versions require 4.4GB as minimum
HOW TO Avoid Wubi & Install Ubuntu 10.04 on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

      
 Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)

      
 With SSD or Flash (trim does not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sdb1
sudo tune2fs -o discard /dev/sdb1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.

---

