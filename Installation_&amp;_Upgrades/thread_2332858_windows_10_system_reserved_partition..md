---
title: "windows 10 system reserved partition."
date: 2016-08-04
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2016-08-04
I did a fresh install of windows 10 1607 and have 2 partitions.  One is system reserved, the other is c:.  Can I still shrink c: partition and dual boot ubuntu 16.04.1.

Henry

---

### Post by oldfred on 2016-08-04
You should also have an ESP - efi system partition if UEFI. Windows will not show it as a partition except in its partition tools as it is not mounted normally.

Best to use Windows own partition tools to shrink the NTFS partition. And reboot immediately so it can run chkdsk.
Make sure fast start up or always on hibernation is off. And in UEFI make sure fast boot is off at least until system is fully reconfigured.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 10 screens or similar to Windows 8
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)
UEFI install,windows 8 with Something Else screen shots, similar for newer versions of Ubuntu
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

---

