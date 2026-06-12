---
title: "Ubuntu 10.04 Inst. with raid ?"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by 1024Jon on 2011-09-25
I've searched around in the forums and I apologize if this has been posted before but I'm unable to find anything that fits this problem exactly.  I'm trying to install 10.04 on a single drive, and have a separate raid 0.  The raid 0 shows ok on the live cd, and installing onto the single disk works fine, but when I go to boot, I get "grub no such disk".  With the raid disconnected, all is fine, but once its connected nothing will boot.  I've tried single sata and ide drives.  I've tried to install with the raid attached so the /dev/sd* will match on grub and I've tried to boot to the live cd after the installation and running the boot repair([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)).  Everything I try seems to fail.  I'm aware that there could be a compatibility problem with the raid controller, but I'm hoping that maybe someone else has some insight.  

Thanks

---

