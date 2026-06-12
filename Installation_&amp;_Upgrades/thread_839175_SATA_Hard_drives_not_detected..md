---
title: "SATA Hard drives not detected."
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by SillyChild on 2008-06-24
Hi everyone,

I'm trying to install Hardy Heron on my desktop but it is cannot detect my SATA hard drives.

My system configuration is as follows:
Intel Core 2 (Quad E9300)
Mother Board: Asus P5Q-E
Graphics Card: Asus 512MB 9600 GT
RAM: 2GB 1066Mhz
HDD 1: Seagate SATA 300GB
HDD 2: Seagate SATA 320GB

Bios can detect both the HDDs and I know that there is nothing wrong with the hardware, because Windows XP was installed in this earlier. Now when I try to install Ubuntu, it cannot detect the hard drives (including when running with live CD).

This thread: [http://ubuntuforums.org/showthread.php?t=768859](http://ubuntuforums.org/showthread.php?t=768859) did mention about using some boot options, but when I tried the option all_generic_ide, it got into a Kernel Panic.
```
Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(104,1)
```

I have also checked with errors on the disk and MD5SUM checks and it is all good. Any guide will be helpful.

Cheers.

---

### Post by Pumalite on 2008-06-24
Your board must have at least 4 SATA ports. Try switching ports.

---

### Post by SillyChild on 2008-06-24
It has 6 ports. They are connected to 1 and 2. I'll try changing them now and see if it makes it any better.

---

### Post by SillyChild on 2008-06-24
Tried vaious combination with just one HDD, still no luck :(

---

### Post by simvin76 on 2008-06-24
I had problems with SATA when I was installing Gentoo (other distro).
I couldn't find the article, but you had to do something special to get the Intel SATA chipset to work. Find out what chipset you have (use lspci) and you will probably find a forum post about it.

I had to recompile the kernel by hand (it is the Gentoo way).

---

### Post by SillyChild on 2008-06-25
Today I tried to install Fedora and it was the same problem. However, it worked perfectly when I tried to install Win XP, it was ok. So I know for sure that it is not a hardware issue, but most likely a kernel issue.

As I don't have another spare PC with me I don't have a way to recompile the kernel. This is becoming a total pain now... arrgghhhh.. :(

---

### Post by Pumalite on 2008-06-25
Try your luck at some boot parameters:
Boot parameters
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
Try the most common one first:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off all_generic_ide vga=0x317 vga=788 vga=789 vga=791
To be tried alone or in different combinations until you hit the right one.

---

### Post by SillyChild on 2008-06-28
Problem solved!!!

This is what had to be done:

Change SATA Access from IDE to AHCI (although I have heard that Windows XP can cause problems - read this thread for the solution: [http://vip.asus.com/forum/view.aspx?id=20080627002442234&board_id=1&model=P5Q-E&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20080627002442234&board_id=1&model=P5Q-E&page=1&SLanguage=en-us)).

Use the Intel Ports (SATA 1 - 6), not the SIL5723 ports that connect through the Marvell 88SE6121.

Hope that helps anyone who face this problem.

---

