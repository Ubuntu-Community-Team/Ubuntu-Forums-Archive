---
title: "Dual Boot Ubuntu on top of Windows and Phoenix OS"
date: 2018-05-26
forum: Installation &amp; Upgrades
---

### Post by narutovps on 2018-05-26
I have installed Windows 7 and Phoenix OS (Dual Boot) and now I want to install Ubuntu(Dual Boot). So will both Windows and Phoenix OS will be added on GRUB boot menu or only windows??
If only windows is added then is there any way to add Phoenix OS as well??

---

### Post by yancek on 2018-05-26
If you are using windows 7, the default is an Legacy/MBR install so the installer should detect that and do a Legacy install of Ubuntu.  If you leave the default for bootloader installation (/dev/sda) the Ubuntu Grub should install to the MBR and include menuentries for other operating system,  If that fails, you can run sudo update-grub after installing and booting Ubuntu.  I don't know Phoenix OS so can't say for certain it will be detected, if it is a Linux system, probably.

---

