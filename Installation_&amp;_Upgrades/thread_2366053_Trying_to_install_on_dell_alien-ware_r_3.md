---
title: "Trying to install on dell alien-ware r 3"
date: 2017-07-13
forum: Installation &amp; Upgrades
---

### Post by smccann on 2017-07-13
First time does not boot (scrambled  graphics ) 
Disabled secure boot and UEFI got t installation screen got a error     rebooted  got further noticed installer was slow but functional  got  to the installing grub loader part and error out with Executing 'grub-install /dev/sda' failed. This is a fatal error.
tried a couple of other flavors of linux got a couple to install but I want Ubuntu
any ideas 
Steve

---

### Post by oldfred on 2017-07-13
Do you have RAID or Intel SRT that looks like RAID?
If RAID 0, half of data is on one drive and half on other, do not turn RAID off without full backup as you destroy system.

Older version:
 Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr](http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr) 

Since Dell based may be similar:

 Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)

---

