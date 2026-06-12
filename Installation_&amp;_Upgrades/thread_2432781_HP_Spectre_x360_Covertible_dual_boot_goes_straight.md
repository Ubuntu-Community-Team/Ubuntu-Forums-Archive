---
title: "HP Spectre x360 Covertible dual boot goes straight to windows 10"
date: 2019-12-08
forum: Installation &amp; Upgrades
---

### Post by alejom200 on 2019-12-08
Hello,

I have a HP Spectre x360 Covertible and it is not booting into GRUB. Instead, it is going straight to windows.

I uncheck the fastboot from Windows 10, disabled secured boot.


The error code with the boot fix tool is the following:
[http://paste.ubuntu.com/p/g5y3Ct3xzs/](http://paste.ubuntu.com/p/g5y3Ct3xzs/)

Please help!

Thanks,

Alex

---

### Post by oldfred on 2019-12-08
Have you changed drive settings in UEFI from RAID or Intel RST to AHCI.
If dual booting with Windows you must first install Windows AHCI driver or it will not boot.

       HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
HP Envy x360 with Core i5-10210U Intel UHD Graphics Hardware Acceleration 
[https://ubuntuforums.org/showthread.php?t=2432438](https://ubuntuforums.org/showthread.php?t=2432438)
[Guide] Install Ubuntu 18.04 on HP Spectre x360 13" 
[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086)
[https://ubuntuforums.org/showthread.php?t=2422113](https://ubuntuforums.org/showthread.php?t=2422113)
See last post for many boot parameters, still using UEFI, not Legacy
[https://ubuntuforums.org/showthread.php?t=2407615](https://ubuntuforums.org/showthread.php?t=2407615) &
[https://ubuntuforums.org/showthread.php?t=2406993](https://ubuntuforums.org/showthread.php?t=2406993)
[https://askubuntu.com/questions/1161563/external-hdd-works-on-desktop-but-not-recognized-on-laptop](https://askubuntu.com/questions/1161563/external-hdd-works-on-desktop-but-not-recognized-on-laptop)

---

