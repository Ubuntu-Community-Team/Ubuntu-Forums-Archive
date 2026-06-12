---
title: "Can't run or install hardy - stops at initramfs prompt"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by reja on 2008-07-29
I am trying to install Hardy (64-bit) on a newly built system (AMD Athalon 64 X2, GeForce 8200 board). Whether trying to run live or install, it goes through the Ubuntu splash screen, then drops to a "initramfs" prompt. 

What I've tried so far:

[LIST]
[*]ran F6, entered various combinations of "all_generic_ide", "floppy=off", "irqpoll". No change.
[*]Reconfigured bios to default, removed vga irq in bios, fiddled with various irq configs. No change.
[*]Disabled floppy in bios. No change.
[*]Enabled floppy in bios. No change.
[*]Disconnected IDE and left Sata. No change.
[*]Disconnected Sata and left IDE. No change.
[*]Tried to boot off old working 32-bit copy of Hardy on old IDE drive. Went through grub, then dropped to initramfs prompt again.
[/LIST]

Please help this poor old grandma who is dying to use her new system! Thanks.

---

### Post by wpshooter on 2008-07-29
Download, burn & try to install from the ALTERNATE (texted based) CD version of Ubuntu.

---

### Post by P.i.R.h.o. on 2008-07-29
I've got the same problem, and I already tried the alternate CD.  Checked the MD5 signature, burnt at 4x.  The installer starts, but when it starts checking the CD, it returns with the message that the CD is not a valid Ubuntu disc.

When I "ls" it, the output says something like "./install: input/output error".  "dmesg" shows reading errors on the CD device.

---

### Post by P.i.R.h.o. on 2008-07-29
Problem solved by installing Gutsy and then upgrading it to Hardy.  Maybe not what I wanted to do initially but hey, it works :)

---

### Post by reja on 2008-07-30
I finally got Hardy to install by doing the following:

Initially I had a hard drive (master) and CD-ROM (slave) running off on-board IDE, in addition to the SATA hard drive. I disconnected the IDE hard drive and left the CD-ROM on IDE. Tried various new jumper configurations of CD-ROM; drive was finally recognized when set to CS (cable select). Tried to reinstall Hardy, same problem. Then tried reinstalling with this added to the F6 boot command:

"all_generic_ide floppy=off irqpoll"

This time: SUCCESS!

Note that the boot option listed above did not work until I reconfigured the IDE drive(s). The installation now works perfectly, reboots with no problem (other than the typical nVidia nonsense). I have not tried reinstalling any IDE hard drives.

Thanks to all who replied. Now, on to the configuration headaches...

---

