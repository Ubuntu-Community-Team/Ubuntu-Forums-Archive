---
title: "Live CD in UEFI splashscreen stays black"
date: 2013-04-10
forum: Installation &amp; Upgrades
---

### Post by Aiken Pandora on 2013-04-10
hey,
i got this problem, as soon as I start the Linux Live-CD with UEFI, the grub-bootloader loads, but as soon as i try to start Ubuntu the screen just turns black. You hear that the CD-Drive is running but nothing happens and after some time it just stops.
No matter if I try to start with UEFI on a USB-Drive or Live-CD i can´t get beyond the grub2 bootloader...
I tried nomodeset and xforcevesa. 

Anyone got an idea?

and i already tried IDE instead of AHCI.

System is:
i3770k
Gigabyte z77x-UD3H
Nvidia 570GTX (i think, could be an 570 GT to or so)

---

### Post by oldfred on 2013-04-10
You probably need nomodeset. I have to use it on every live install boot and first boot after install until I get nVidia drivers installed.

At grub menu press e and add nomodeset in place of quiet splash on linux line.

       Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Aiken Pandora on 2013-04-10
i tried nomodset before, it doesn´t work. Like xforcevesa.
I also tried it with vga=1280x1024 or other resolutions.

maybe i should add, that starting CD or USB in Bios Mode works perfectly fine.

---

### Post by Aiken Pandora on 2013-04-10
its like nothing happens, after i use F10, the screen just gets black and thats all, even without quiet splash and so one.

---

### Post by Aiken Pandora on 2013-04-10
solved it by myself, the Problem was the Bios, i don´t know what, maybe the Bios-Version, but i got a Dual-Bios System so i changed to the Backup-Bios (never used it, but it got the same settings as my default, except the Backup-Bios still has the Default Bios-Version)

---

