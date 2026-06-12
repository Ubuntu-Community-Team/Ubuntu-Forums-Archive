---
title: "Dual Boot: My installation stuck on the Ubuntu logo screen?"
date: 2018-10-09
forum: Installation &amp; Upgrades
---

### Post by umang11 on 2018-10-09
Recently, I am installing Ubuntu 18 version on alongside Windows 10 but I get installation process get stuck on Ubuntu logo screen. I keep it left but it is proceeding further. Currently, I am using Asus GL553VD? Any navigation or help is appreciated?

---

### Post by oldfred on 2018-10-09
Do not force shutdown. 
       Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term signal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system 
    
Have you updated UEFI from Asus?
Your NVMe SSD may also need firmware update.

You have nVidia, and need nomodeset to install & first boot after install or until you install nVidia proprietary driver from Ubuntu repository.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Many also need another boot parameter. pci=nomsi
How to install Ubuntu on ASUS F556U, JournalError error?
[https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error?noredirect=1#comment1776854_1079540](https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error?noredirect=1#comment1776854_1079540)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

---

