---
title: "noob needs help"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by callenc123 on 2008-04-13
i am trying to install 7.10 on an hp visuilize x class workstation and i took off the quiet splash to see the error code  and it is as follows 
run-init: /sbin/init: I/0 error

and then i get kernel panic attepted to kill init !

---

### Post by Pumalite on 2008-04-13
I have no idea of workstations. Looks like hardware incompatibility. Try the Alternate CD first. If not we can try some boot parameters.

---

### Post by callenc123 on 2008-04-13
dont have alternet cd and no blank cds can we try boot paramiters

---

### Post by callenc123 on 2008-04-13
i can get all hardwear info if you need it

---

### Post by Pumalite on 2008-04-13
Here is a collections of guides and parameters to try:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)

Start with the most common:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317 vga=791

To be tried alone or in different combinations.

---

