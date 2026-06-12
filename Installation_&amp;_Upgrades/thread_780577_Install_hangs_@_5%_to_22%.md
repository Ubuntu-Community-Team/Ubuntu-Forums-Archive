---
title: "Install hangs @ 5% to 22%"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by mnord00 on 2008-05-03
Kubuntu 8.04 Live CD boots up, display is fine, I can get on the internet etc. But when I install and it starts to partition it  stops at anywhere from 5% to 22% and then gives an error Temp too high (127 c) shutting down. I went to the bios and checked the temp and it was at 51c. I tried Kubuntu 7.10 and had the same results. I have an ECS GV750VT-M mother board. Can anyone tell me what to do. I think I have to change something in my Bios but I do not know what. If I need to hit F6 to set perameters, I need info on that as well.
Thanks

---

### Post by Pumalite on 2008-05-03
Burn a new CD. Follow this guide>
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum, burn at 4x or less in good quality CD-R, check CD integrity before install.

---

### Post by mnord00 on 2008-05-04
I tried your suggestion and the cd passed the integrity check. I also used the cd to install on another pc. The install went just fine on the other pc. I think I have a hardware incomparability problem, but I am not sure which direction I should go. Thanks for your help

---

### Post by Pumalite on 2008-05-04
You can try the Alternate CD, but you might need this anyway:
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

### Post by mnord00 on 2008-05-05
Thank you for all of the web links especially the info on acpi. You have posted this info before, but I could not locate it. I will let you know what resolved my problem.

---

