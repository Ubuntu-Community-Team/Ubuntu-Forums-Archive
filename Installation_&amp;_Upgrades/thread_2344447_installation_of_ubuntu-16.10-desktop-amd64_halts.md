---
title: "installation of ubuntu-16.10-desktop-amd64 halts"
date: 2016-11-25
forum: Installation &amp; Upgrades
---

### Post by tevang2 on 2016-11-25
Can someone please tell me why the installation halts?

[https://dl.dropboxusercontent.com/u/48168252/IMG_20161125_181214.jpg](https://dl.dropboxusercontent.com/u/48168252/IMG_20161125_181214.jpg)

---

### Post by ian-weisser on 2016-11-25
Well, if it choked on systemd-udevd.service, then I would suspect incompatible or defective hardware.

Do you have access to the Live environment?

---

### Post by tevang2 on 2016-11-29
This is the screen messages I get when I try to run Ubuntu live:

[https://dl.dropboxusercontent.com/u/48168252/Link%20to%20IMG_20161129_171048.jpg](https://dl.dropboxusercontent.com/u/48168252/Link%20to%20IMG_20161129_171048.jpg)

[https://dl.dropboxusercontent.com/u/48168252/IMG_20161129_172208.jpg](https://dl.dropboxusercontent.com/u/48168252/IMG_20161129_172208.jpg)

In case this looks like a hardware compatibility issue, these are my laptop's specifications:

[http://www.ultrabookreview.com/8975-asus-rog-gl552vw-review/#a1](http://www.ultrabookreview.com/8975-asus-rog-gl552vw-review/#a1)

Maybe it's due to the Skylake Intel processor it has. For the record I haven't used my new laptop since when I bought it in May (!!!), because I could not make any Linux distro work properly! Any idea how to fix it?

---

### Post by oldfred on 2016-11-29
The nVidia chip almost always needs nomodeset whether booting with UEFI or BIOS.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]https://wiki.ubuntu.com/Kernel/KernelBootParameters

[/URL]
 ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3)
[http://ubuntuforums.org/showthread.php?t=2327570](http://ubuntuforums.org/showthread.php?t=2327570) 

[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]
[/URL]

---

