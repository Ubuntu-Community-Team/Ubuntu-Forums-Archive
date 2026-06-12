---
title: "No GUI with 8.04 live cd"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by archerry on 2008-05-07
I cannot boot to the GUI using the new live cd.
I just get  the text command line (the disc works fine on other machines including another laptop.)
Hardware is a Mitac 8375x with 512MB RAM.
Video is "uni chrome GFX integrated in KN400A chipset."
This unit has simply worked well with previous releases, currently 7.10.
How do switch on the Verbose bootstrap option? (to help investigate the problem.)
(The "vga=771" option produces the same text in a smaller font.)

---

### Post by Pumalite on 2008-05-07
Try:
vga=791

---

### Post by archerry on 2008-05-08
vga=791 did not work, it just made the text even smaller.
One message I did spot was to try "pnpbios=off" but that didn't work.
Is there a verbose boot option?

---

### Post by Pumalite on 2008-05-08
You can try the Alternate CD and or use these boot parameters; to be tried one by one or in different combinations:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317

---

### Post by archerry on 2008-05-21
I gave up trying the direct method.
I formatted the disc, installed 7.10 again and then did a 'version upgrade' through 'adept manager.'
This worked well, but it did take a long time!

---

### Post by Pumalite on 2008-05-21
Congrats!

---

