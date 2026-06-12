---
title: "help me with triple boot please"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by Zireth ZH on 2010-06-14
im running windows 7, installed kubuntu after and now i wanna install another distro somewhere.. i dun want to see only one of the linux distros and windows 7 in the grub menu the next time i boot once i finish the installation...

can someone guide me on this process?

---

### Post by oldfred on 2010-06-14
You have to decide whose boot loader you want in control. If you want Ubuntu's grub2 in charge you either to do not install the boot loader from the second install, or install it to the PBR or partition boot sector that the second install is in. If it does not let you choose you can easily just reinstall grub2 to the MBR. sudo update-grub should find the other install.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

