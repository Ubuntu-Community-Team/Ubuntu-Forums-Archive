---
title: "Boot Repair for windows partition"
date: 2014-10-13
forum: Installation &amp; Upgrades
---

### Post by gpestana on 2014-10-13
Hi,

I'm usign a windows OS in one of my laptops and it turns out - as would be expected at some point - I am having problems. The already mytical blue screen appeared and now the OS is not recognized when booting. 
I've tried the boot-repair tool to solve the problem (1st time here) and it ouput this log: [http://paste.ubuntu.com/8551170/](http://paste.ubuntu.com/8551170/)

I'm trying to check what can I do. Even considered to install grub or lilo to boot windows (the SSD has only windows int it). I'm wondering if you could give me a hand on this.

Thanks,
gpestana

---

### Post by Dennis N on 2014-10-13
From what I see from boot info script, sda is your 2 gB flash drive (containing installer) and sdb is a 24 gB SSD drive.  sdb has an msdos partiton table and one primary partition (type 73) using the entire disk (see lines 41-50).  The type of partion is Microsoft Reserved partition. There appears to be nothing else on the SSD.

Should Windows or Linux be installed on the SSD? But there is no evidence of that. What happened here?

---

### Post by gpestana on 2014-10-13
Yes, indeed. I have no idea what happened here, but I start to suspicious that the whole OS was destroyed for some reason - most likely virus - and then the blue screen appeared.

---

### Post by oldfred on 2014-10-13
What model computer?
Is this an UltraBook type system. That has a small SSD typically 16GB to 32GB and is just cache using Intel SRT. 
If that is the case, your hard drive is not showing at all.

Generally Boot-Repair can only do minor repairs to Windows systems. It can reinstall a Windows boot loader for BIOS/MBR systems, not UEFI and run ntfsfix which really only sets a chkdsk flag for Windows to run chkdsk for corrupted drives.

Best to use Windows tools and have a Windows flash drive for repairs. Have one for the current version of every operating system you have. I think all these are really the same instructions:
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

