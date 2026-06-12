---
title: "Can't load ubuntu 11.10 from grub after upgrading"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by sashacea on 2012-10-09
Hey everyone, I am a somewhat newbie to linux, running dual boot with Windows 7 on my Samsung netbook.

I started by installing ubuntu 10.10 (Maverick Meerkat) and everything went fine; great even (runs much more smoothly than Windows 7 on my netbook). After a while I upgraded to 11.04 (Natty Narwhal) but I had to run it on a low-graphics session every time, if not it wouldn't leave the purple ubuntu screen.
I just now upgraded to 11.10 (Oneiric Ocelot), and I cannot get past the purple screen, and I have not found a way to leave grub (I haven't found a way to at least run it in low-graphics mode).

Any help / codes? Thank you!

---

### Post by oldfred on 2012-10-09
Welcome to the forums.

Most users are jumping to 12.04 since it has long term support.

From the older versions to the newer kernels they incorporated some video into the kernel. Then you need settings like nomodeset to boot and then install the proprietary drivers if nVidia.

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)
Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

