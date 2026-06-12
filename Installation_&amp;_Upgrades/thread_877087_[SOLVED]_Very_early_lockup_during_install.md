---
title: "[SOLVED] Very early lockup during install"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by rbstern on 2008-08-01
I'm trying to install 8.04.1 server edition and getting a lockup right after the startup of the Caldera DR-DOS.  Immediately following the line "EMM386: Warning: Address line A20 already enabled", the system freezes and requires a hard reboot.

Problem occurs with both the x86 32bit and alternate AMD 64 bit versions.  I have tested the 32 bit CD on another machine, and it boots past this point without problem, so it's not the CD.

Hardware (all new, except the CD drive):

ECS GeForce6100PM-M2
AMD Sempron LE1250 (64 bit)
1GB PC2-5300 RAM
(2) WD Cavier 250GB SATA
Yamaha CRW2100E

Sequence from components out of the box:

Installed hardware.  Booted to bios.  Set the hard drives into a bootable mirrored RAID array via the Nvidia RAID bios.  RAID status shows disks as healthy.

I have tried the following, each resulting in the same lockup:

- Removed the RAID configuration
- Set bios to Fail Safe Defaults
- Set bios to Optimized Defaults
- Attempted with only one drive installed

In the last configuration, I booted a Windows 2000 Professional setup CD.  Windows 2000 went through it's driver loading and offered to install on a partition I created.  I suspect the hardware is good.

I'm at a loss for what to try next.

EDIT: Failed to list this important step:  After the first several attempts, I also flashed the motherboard bios with the latest version from ECS' web site.

---

### Post by Partyboi2 on 2008-08-01
Have a look at this:
[http://www.nforcershq.com/forum/1-vt69269.html?start=0](http://www.nforcershq.com/forum/1-vt69269.html?start=0)

---

### Post by rbstern on 2008-08-01
I found that about an hour before you posted, was just coming back to post the link.

Thanks for doing the legwork!

---

