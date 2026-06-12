---
title: "Installation hangs on every boot"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by QwUo173Hy on 2011-10-16
The boot up hangs as shown in the attachment. I don't know where to start. The live CD session ran fine.

 My graphics card is Nvidia. I've tried setting the graphics mode to "text" in grub.cof. I have yet to log in to the system graphically.

---

### Post by QwUo173Hy on 2011-10-17
Nevermind - I reinstalled 11.04. I'll install 11.10 on a spare partition in a few weeks and check it from time to time to see if it works yet or if any more fixes become available.

I did get it to boot to a desktop, but my PS2 mouse wouldn't work (but the PS2 keyboard did). And the USB keyboard wouldn't work. Then I installed the 3D graphics driver and lost my network .. even eth0. I'm not confident in the release in it's current form, on my hardware. But damn I'm envious of those of you that have a working system. It looks amazing!

---

### Post by oldfred on 2011-10-17
I had some trouble with USB mouse & keyboard several versions ago until I enabled USB mouse & keyboard in BIOS. Some also said turning off fastboot/quickboot or whatever in BIOS helped.

Sometimes other BIOS settings or boot parameters are required to make it work. With nVidia I always have had to use nomodeset from 10.04 until 11.10 on first boot.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by QwUo173Hy on 2011-10-18
> **oldfred said:**
> I had some trouble with USB mouse & keyboard several versions ago until I enabled USB mouse & keyboard in BIOS. Some also said turning off fastboot/quickboot or whatever in BIOS helped.

Sometimes other BIOS settings or boot parameters are required to make it work. With nVidia I always have had to use nomodeset from 10.04 until 11.10 on first boot.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)
Thanks a lot oldfred. I'm lucky to get such a detailed reply at release time! I'll try in the next few days and come back with an update.

---

