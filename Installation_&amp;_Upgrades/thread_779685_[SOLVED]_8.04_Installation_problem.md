---
title: "[SOLVED] 8.04 Installation problem"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by kgriff on 2008-05-02
I am trying to install Hardy on a homebuilt computer using the alternate CD.  The installation process seems to progress fine for a while, until it gets to the ¨Detecting Hardware¨ phase.  At this point, I see a progress bar on the screen, the last text I see flash up is ¨Starting PC Card Services¨, then it doesn´t progress to the next step in the install.  I don´t think the hardware detection is the issue, though, because it does seem to successfully complete this step.  I believe it is the step that follows that hangs up, though I don´t know what the next step is.
Anyone have any suggestions that might get me past this point in the installation?

System specs:
motherboard:  Asus A7V 133
Processor:  1000 MHz Athlon
Video:  ATI Radeon 9000
Audio:  None
Ethernet:  Some generic 10/100 thing
Promise ATA100 controller on mobo
RAM 1GB

---

### Post by Pumalite on 2008-05-02
Are you wired to the Internet?

---

### Post by kgriff on 2008-05-03
Yes, I am wired to the internet.

---

### Post by Pumalite on 2008-05-03
Here are some boot parameters to try:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

Try the most common ones first:
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317 vga=791

---

### Post by kgriff on 2008-05-04
That took care of it.  Thanks.

---

### Post by Pumalite on 2008-05-04
You are welcome. Good luck.

---

