---
title: "Dual Booting Fiesty and XP"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Luigi239 on 2007-04-22
Hello, I plan on doing a clean install of Windows XP, and then creating a 10gb Fiesty partition on the same drive. I am assuming that I just use Gpart on the live CD to partitian the drive. But, after I install, how will I set Grub to auto-boot to XP, not Ubuntu, as the other person using this computer wants nothing to do with linux. (:(). Will I still be able to install all windows updates after installing Fiesty? (I dont know if grub would screw it up...)

Thanks for helping an Ubuntu nub out. :)

---

### Post by pepsi_max2k on 2007-04-22
once grub's installed you can change which os loads by default by changing the number for "default" in /boot/grub/menu.lst. it won't affect how windows works at all.

---

