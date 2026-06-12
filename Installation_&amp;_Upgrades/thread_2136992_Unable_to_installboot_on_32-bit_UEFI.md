---
title: "Unable to install/boot on 32-bit UEFI"
date: 2013-04-19
forum: Installation &amp; Upgrades
---

### Post by dabigjhall7 on 2013-04-19
Hi, I just got a Samsung xe500t1c laptop and am trying to install Kubuntu on it.  This laptop is UEFI-only (no BIOS compatibility that I can find), and it also has a 32-bit processor.  I haven't found any distributions that support UEFI booting in 32-bit, so I've been trying to boot the installer using 32-bit rEFInd and Grub 2.

rEFInd and Grub 2 seem to work correctly, but I can't get the kernel to boot from there.  I've tried Kubuntu 12.10, 13.04 beta 2, Fedora 18, Linux Mint, and a few others.  I have one flash drive with rEFInd and Grub 2 on it, and a second that I put the installer on.  I also installed Kubuntu 13.04 beta 2 from another computer on a USB hard disk and tried to boot that.

Trying to run from rEFInd (using a menu entry or the shell) always produces "Failed to open initrd".  Using Grub 2, nothing happens at all - the grub command prompt stays on the screen.  Adding "debug" to the kernel parameters doesn't change anything.  I compiled a kernel with built-in initrd and command line, that does nothing from either shell.

Does anyone have any suggestions about a different kernel or distribution to try, or any way to figure out why the kernel isn't booting?  Thanks!

---

### Post by oldfred on 2013-04-19
Unless Intel or some Linux created a workaround, it looks like it is not supported.

 [http://en.wikipedia.org/wiki/Atom_%28system_on_chip%29]("http://en.wikipedia.org/wiki/Atom_%28system_on_chip%29")
While Penwell SoC supports, in addition to Microsoft Windows, both Linux and Android operating systems, Intel has announced that it won't provide support for Linux on Cloverview family of Atom systems-on-a-chip.[49][50] This announcement has caused strong negative reaction from open source proponents.[51] A few days later Intel issued a statement saying that it has &#8220;plans for another version of this platform directed at Linux/Android"[51][52]

---

### Post by dabigjhall7 on 2013-04-22
Thanks, I hadn't even considered that the CPU might not be supported.  I tried compiling Linux 3.9 rc7 just for fun and still no luck.  I'm returning it and getting something else.

---

