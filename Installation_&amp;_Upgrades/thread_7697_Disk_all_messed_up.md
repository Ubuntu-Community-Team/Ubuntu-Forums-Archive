---
title: "Disk all messed up"
date: 2004-12-10
forum: Installation &amp; Upgrades
---

### Post by Frox on 2004-12-10
I tried installing 4.10 for AMD64 today.
Like a few other people have reported, GRUB hung at stage 1.5 for me. I then tried to boot from my WinXP CD to repair the mbr, but nothing happened. The same goes for the Win98 CD and win98 boot floppy. Trying to boot freedos resulted in a divide by zero error. Fortunately, my old Knoppix disk did boot, and after installing that (which overwrote GRUB with LILO) I was able to get into Windows and install the recovery console. Although fixmbr did revert my system back to the default Windows bootloader, it didn't fix the problems of booting dos. The WinXP installer still won't load, freedos still tries to divide by zero, and I can't even boot my hard drive install of dos from the XP boot menu. Additionally, Partition Magic reports that my partition table is bad even though I still have access to all the drives.
It may also be worth noting that disabling this hard drive in the bios does allow dos disks to boot up.

Does anyone know what's going on here?
Any fixes that won't require me to have to format my drive?
I'm at a bit of a loss here...

---

