---
title: "Fedora over ubuntu"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by sknowonweb on 2011-06-26
Hi ,
I was using ubuntu 11.04 with a separate boot partition . Then i installed fedora 15 during which i erased(format) the /boot partition which holds the Grub2 entries for ubuntu . And its been replaced with the Grub's of Fedora .
 My Ubuntu installation is still intact sans the /boot folder . 
i tried copying the ubuntu vmlinuz and initrd into /boot (now belonging to fedora) and booted from grub - it throws me into initramfs , from which i dont know how to get into the lovely GUI of ubuntu . 

My fdisk -l is 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      530144      265041   83  Linux
/dev/sda2        51199216   488392064   218596424+   5  Extended
/dev/sda3          530145    51199154    25334505   83  Linux
/dev/sda5        51199218   153597464    51199123+  83  Linux
/dev/sda6       153597528   255995774    51199123+  83  Linux
/dev/sda7       255995838   358394084    51199123+  83  Linux
/dev/sda8       358394148   460792394    51199123+  83  Linux
/dev/sda9       485371908   488392064     1510078+  82  Linux swap / Solaris
/dev/sda10      460792458   485371844    12289693+  83  Linux

where /sda1 is boot ; /sda7 is home ; /dev/sda10 having the [once] ubuntu installed files without /boot folder ; /dev/sda3 my fedora installation from where am typing this .

Can i make a dual boot of ubuntu and fedora now **without** the need of reinstalling ubuntu again ( i dont wanna loose my personalisations of ubuntu ) . ????

---

### Post by zealibib slaughter on 2011-06-26
Follow the instructions in the following link to reinstall grub 2 and that should give you both choices of fedora and ubuntu at the grub prompt [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

