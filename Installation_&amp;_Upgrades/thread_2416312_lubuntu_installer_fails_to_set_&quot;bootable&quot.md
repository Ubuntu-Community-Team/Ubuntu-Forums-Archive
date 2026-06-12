---
title: "lubuntu installer fails to set &quot;bootable&quot; flag in boot partition"
date: 2019-04-08
forum: Installation &amp; Upgrades
---

### Post by steve.m on 2019-04-08
Hi, please consider this to be a bug report.

I installed lubuntu on a relatively old computer (an Intel Atom D510MO).  On trying to run the installed system, the computer BIOS displayed a message about no bootable device found.  After many false starts at debugging this issue, I pulled out the disk with the installed lubuntu on it and tried it on another, more modern, computer.  That computer had no trouble booting the system.   I finally narrowed down the problem to the "bootable" flag on the lubuntu partition.  After the disk partition was set to be bootable, the old computer runs the system with no problem.

The old computer has an old hard drive, about 4 years old, with a standard Ubuntu system on it.  That hard drive has the boot partition marked bootable.  I did not set that flag.  The drive was brand new and the installer used the whole drive for linux.  So, I think it was not long ago that the Ubuntu installer knew to set the bootable flag.   

Granting that most computer BIOSes now are smarter,  I think that failure to support innocent old hardware with old-fashioned BIOS constitutes a bug in the linux installer.  Ubuntu people, please fix the installer!

---

### Post by DuckHook on 2019-04-09
Welcome to the forums steve.m,

The forums are not part of Canonical. Our connection to Ubuntu is purely that of a collective of general users (much like yourself) wishing to contribute to the community by volunteering our time and expertise to assist each other. The developers rarely, if ever, visit here.

To report a bug, please [read through this]("https://help.ubuntu.com/community/ReportingBugs").

From one user to another, it's good to know that you found a solution to your problem.

Good Luck and Happy Lubuntu-ing.

DH

---

### Post by oldfred on 2019-04-09
We have seen this issue before, mostly on Intel motherboards.

Grub legacy or grub2 do not use boot flag. Windows and the generic syslinux boot loader do use boot flag.
So a Linux install would not normally have a boot flag for BIOS boot.

We also found this with gpt partitioned drives. With gpt only the ESP - efi system partition is supposed to have the boot flag. But to make some Intel boards boot in BIOS mode we had to add a boot flag. With gpt a bios_grub partition is normally all  that is required for BIOS boot.

---

