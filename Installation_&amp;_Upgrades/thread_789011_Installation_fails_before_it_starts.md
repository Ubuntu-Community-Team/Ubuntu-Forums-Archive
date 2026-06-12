---
title: "Installation fails before it starts"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by Zyndrof on 2008-05-10
Hi!

Yesterday I installed Ubuntu without any problems on a laptop, which indicates no trouble with the CD I'm using. When I try to install it on my desktop though, it just wont work.

I believe there is a problem regarding the booting. I have set the booting order in the setup menu so that the CD/DVD-ROM is first in order. When I check the boot menu though, nothing have changed.

The CD runs though and I get to the first menu where I choose to Install Ubuntu. I see the loading screen and then a lot of text is printed on the screen which is hard to make any sence out of, but I guess it says that the installation process was locked. I get no further from here.

I tried the option of "Help me run from CD" without any success.

My computer is a three year HP Pavilion.

What should I do?

Thank you in advance!

---

### Post by Pumalite on 2008-05-10
Try the Alternate CD.
Here are a few links om all kinds of HP:
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)
[http://aldeby.org/blog/?page_id=87](http://aldeby.org/blog/?page_id=87)
[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)

---

### Post by Zyndrof on 2008-05-10
I tried the Alternate CD and also some of the codes provided on the sites you linked. But it still wont work. I cannot figure out the problem.

By the way, I don't have a HP laptop but a desktop if that makes any difference. The boot menu is version 3.04.

Thank you

---

### Post by Pumalite on 2008-05-10
You might need some boot parameters. Here are some guides and collections of them. Try your luck:
Boot parameters
                                                                                                                                                                                                                                                                                                                                                                                                                                    [http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317 vga=791

---

### Post by Zyndrof on 2008-05-10
The VGA part of your boot parameter caused problems, but I accessed the installation with **noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off**. It seems it inactivated my USB-ports though as my mouse and keyboard stopped working. I've read that can happen with **noapic**.

How can I keep this from happening?

---

### Post by Pumalite on 2008-05-10
Use the boot parameters one by one and start adding others until you find the right combination.

---

### Post by Zyndrof on 2008-05-12
Okay, I have now been able to locate the parameters that let me access the install menu. The problem is that no matter how I combine them the USB ports are shut down and I cannot use the mouse nor the keyboard making it impossible to actually perform the installation.

The working boot parameters are as following:
**acpi=off (lacpi=off) pci=noacpi irqpoll**

How can I prevent the USB ports from shutting down?

Thank you,
Zyndrof

---

