---
title: "Sony Vaio Dual Boot Step Wise Installation"
date: 2013-05-08
forum: Installation &amp; Upgrades
---

### Post by helpseeker on 2013-05-08
Hello, I am a student from India and I have bought Sony VAIO e series laptop(Product name-SVE15128CNB and Model no.-SVE151A11W). I really need to install Ubuntu on my laptop . I have tried various times  to install Ubuntu along with Windows 8 on my Laptop but every time either it gets installed in legacy mode(its not good as every time I have to go into Ubuntu I have to switch Boot mode) or when I installed it in UEFI mode as per instruction on [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
, I was unable to access my Windows partition.I have read nearly all post related to dual boot problem but I am unable to solve my issue related to dual.
Some posts on Sony community said that Sony does not support dual boot but I wonder if no one having Sony VAIO had ever installed Ubuntu on their laptop. I have already recovered my Laptop 3 times since December
So I request to help me out with my problem . It will very kind if someone can tell me step wise(take care that i am a beginner) process to install Ubuntu(dual boot) on a Sony Laptop . I hope it will solve problem of lots of people having VAIO.
Thanks in advance.

---

### Post by oldfred on 2013-05-08
Several users have installed different models of Sony with some issues. Generally Boot-Repair is required to fix things and many systems are modified to only boot Windows efi file. So Boot-Repair renames Windows file to backup and boots the secure boot version of grub  (shim file) and signed kernels. And can chain load back to the Windows renamed file.

 Sony Vaio T13 
[http://ubuntuforums.org/showthread.php?t=2127699](http://ubuntuforums.org/showthread.php?t=2127699)
Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)
 Sony SVE15125CXS Notebook  Only could Install in BIOS mode, Boot-Repair to UEFI dual boot works
[http://ubuntuforums.org/showthread.php?t=2126389&p=12562570#post12562570](http://ubuntuforums.org/showthread.php?t=2126389&p=12562570#post12562570)
Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help UEFI screens shown
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)
Sony - manually copy grub efi files & rename to make them work post #3
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony - Manually copied but still some issues.
[http://ubuntuforums.org/showthread.php?t=2093415](http://ubuntuforums.org/showthread.php?t=2093415)
EFI dualboot Ubuntu 12.04 and Windows 8 in Raid0 on Sony Vaio S dual SSD
[http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/)
Sony VAIO with Insyde H2O EFI bios Ubuntu 12.04 Dual Boot 
[http://www.linuxrelease.com/2012/07/sony-vaio-with-insyde-h2o-efi-bios.html](http://www.linuxrelease.com/2012/07/sony-vaio-with-insyde-h2o-efi-bios.html)
sony vaio laptop error: symbol not found: `grub_efi_secure_boot'.
[http://ubuntuforums.org/showthread.php?t=2102083](http://ubuntuforums.org/showthread.php?t=2102083)
So this time installed 12.10, then  booted again from liveCD, made backup of (efi part)/EFI/microsoft/boot and copied all files from /EFI/ubuntu into it. Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works
Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply

---

