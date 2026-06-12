---
title: "Trying to make the switch to ubuntu, but BusyBox hates my computer"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by Damion on 2008-04-11
Hi, everyone, how's it going? I've been trying to make the switch from Windows 98SE and it's frustrating how much trouble I've had with Linux. =( Here's a post I made on a forum that has a support template, to  make it a little easier:

Problem description:
I am currently trying to boot either Ubuntu or Xubuntu 7.10 (Gutsy Gibbon) from a LiveCD so that I can install it. I have almost no Linux experience beyond this project, but was reassured that this would be easy.
On both a factory-shipped ubuntu disk and a home-burnt xubuntu disk, on both of my CD drives, selecting "Start or install", "Start in safe graphics mode" or "Check CD integrity" yields the exact same error. The loading bar appears for a time, and is replaced by a small prompt program called BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7). This prompt displays only (initramfs) for a short time, then spits out pairs of lines with about ten seconds delay between each pair. It looks like this:

```
Busybox V.1.1.3 (Debian 1:1.1.3 - 5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs) [ timestamp.000000] ata 1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen 
[ timestamp.000000] ata 1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in 
[ timestamp.000000] ata 1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen 
[ timestamp.000000] ata 1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in 
[ timestamp.000000] ata 1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen 
[ timestamp.000000] ata 1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in 
[ timestamp.000000] ata 1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen 
[ timestamp.000000] ata 1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in 
[ timestamp.000000] sd 2:0:0:0: [sdb] Assuming drive cache: write through 
[ timestamp.000000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
```
After this text, it just presents a flashing cursor with which you can enter more (initramfs) commands. Nothing more happens, even if you leave the computer on for hours.

Attempted fixes:
I've tried to start it from both a factory-installed ubuntu liveCD and a home-burnt xubuntu liveCD, and tried both these in both drives. I've tried running memtest off of the xubuntu disc, which reported zero errors after eleven passes. I've tried to boot without my external hard drive, which removes the last two "Assuming drive cache: write through" lines, but otherwise changes nothing. I have read the other busybox threads, but none of them appear to have the same error.

Recent changes:
Other than changing the BIOS to permit booting from CD, the only change I've made is to back up everything onto my external to prepare to install linux.

---

Operating system:
Windows 98 SE.

System specs: It's an AuthenticAMD with a AMD Duron processor (1GHZ). A CD-ROM drive, a CD-RW drive, a 19.07 GB HD, a 150 GB external HD, and 502 MB of RAM. Graphics card is a GeForce4.

---

### Post by Pumalite on 2008-04-11
Try the Alternate CD, or, if you can afford it, 8.04 Beta.

---

### Post by warp99 on 2008-04-11
When installing use some parameters as suggested in the boot options guide:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

At the boot menu press F6 and append the kernel line using the options 'acpi=off' and 'irqpoll'. See the guide for a more detailed howto.

---

### Post by Pumalite on 2008-04-11
If Alternate CD doesn't work, here you have more guides and collections of boot parameters to try:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317 vga=791

Try them alone or in combinations.

---

### Post by Damion on 2008-04-11
Thanks for your help! Unfortunately, messing around with that screwed up my external HD and I had to unplug it before Windows would start properly again.

---

