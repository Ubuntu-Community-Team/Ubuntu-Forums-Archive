---
title: "Ubuntu 18 not working on MSI Laptop Gp72m 7rex Leopard Pro"
date: 2018-09-18
forum: Installation &amp; Upgrades
---

### Post by ichaboss on 2018-09-18
Hi, I'm struggling to install Ubuntu 18 on my Msi laptop... Actually the installation seems going well, when rebooting Grub shows but then Ubuntu doesn't boot, black screen... Instead version 16 LTS worked with a few problems but at least it booted! I don't know what to do, can you help me or tell me what I can do to make you better understand my problem? (ex. if there's a way to get a log file etc..)
Thanks!

---

### Post by oldfred on 2018-09-18
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

What video card/chip do you have?

Did you use boot parameters like these with 16.04? they may still be required.

 MSI GS65  Boot parameter: modprobe.blacklist=nouveau 
[https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions](https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions)
MSI GE63 Update UEFI then acpi=off not required
[https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues](https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues)
[https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off](https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off)
MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)

---

### Post by ichaboss on 2018-09-19
Thanks for the quick response. To  answer your question, I have a hybrid system consisting of a Geforce  Nvidia 1050 Ti and an Intel HD Graphics 630. However, I solved the  problem by following the instructions of the first thread:
[  https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions]("http://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions")
So now everything works properly. Thanks again :grin:

---

