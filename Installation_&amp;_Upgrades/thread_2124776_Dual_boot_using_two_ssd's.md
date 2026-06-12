---
title: "Dual boot using two ssd's"
date: 2013-03-12
forum: Installation &amp; Upgrades
---

### Post by Velcio on 2013-03-12
A while back I tried to do a dualboot using my ssd and my hdd that's accelerated using the corsair accelator. That didn't work out as I wanted. I was wondering if it is easy to have a dualboot using two ssd's. I might buy a second ssd for installing ubuntu since ubuntu can't handle accelerated drives. Does anyone have experience with dualboots using two ssd's?

---

### Post by Cheesemill on 2013-03-12
It doesn't matter if you use normal HD's or SSD's or a combination of the 2, it makes absolutely no difference at all to any OS.

---

### Post by Velcio on 2013-03-12
so it should be possible to have windows 7 on one ssd and ubuntu on the other?

---

### Post by Cheesemill on 2013-03-12
Yes.

---

### Post by oldfred on 2013-03-12
You either need to disconnect the Windows SSD or use Something Else and install the grub2 boot loader to the MBR of the Ubuntu drive. Any other install defaults grub2 boot loader to sda which usually is the Windows drive.

 Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

If you have a rotating hard drive for data, you do not need a large SSD for Ubuntu. I have a 60GB SSD but have two / (root) partitions for two different installs in the SSD. All my data is on my rotating drives.

      
 Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

