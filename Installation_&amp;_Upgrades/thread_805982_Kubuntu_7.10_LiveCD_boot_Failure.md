---
title: "Kubuntu 7.10 LiveCD boot Failure"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by MousRcR on 2008-05-24
Trying to install Kubuntu 7.10 and I can't. It goes to the menu (Start or Install Kubuntu...). I can pick any installation method and it shows the blue bar running and then I get the following screen:

_________________________________________________________________
udevd-event [2301]: run-program: '/sbin/ModProbe' abnormal exit

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
_________________________________________________________________

oddly, it runs trough when I have no Hard drives installed.

Any help would be appreciated.  Thx in advance.

---

### Post by Pumalite on 2008-05-24
Try Alternate CD or try your luck at some boot parameters:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
Try the most common first:
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317 vga=791 vga=788
(to be tried one by one or in different combinations until you hit the right one)

---

