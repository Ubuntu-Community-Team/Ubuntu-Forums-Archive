---
title: "HELP! Ubuntu on Intel G33 (Shuttle XPC SG33) install doesnt even load - and ideas?"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by njoubert on 2008-01-28
Hello Everyone!

I recently bought a new Shuttle XPC (SG33G5) with the following specs:

Chipset:  Intel G33 + ICH9DH
CPU: Intel Core 2 Duo E6550 (2.33GHz 64 bit)
HDD: WD Raptor 150GB SATA drive on SATA Channel 0
CD-ROM: IDE drive on IDE-to-SATA chip (JMicron chip on motherboard)

(Full spec is here: [http://us.shuttle.com/barebone/Models/sg33g5_pro_spec.html](http://us.shuttle.com/barebone/Models/sg33g5_pro_spec.html))

I've tried running the 7.10 64-bit DVD, 32-bit CD and 32-bit alternate CD. I burned them all at a low speed (8X) from windows. I tried running 6.06 desktop CD as well. None of these get further than the initial "Loading Linux Kernel" message you get when you enter on the first menu of the CD (the one that comes up right after boot, prompting you to install linux).

I even tried a Debian install, but it claimed that it can't mount my CD-ROM drive...

I've checked around and some people seem to compain about the G33 chipset, but also state that this has been fixed in ubuntu 7.10.

Has anyone had issues with this or has any advice? I've been struggling with this for 2 days and with so little info it's really hard to figure out what's going on...  Any help is appreciated!

---

### Post by Partyboi2 on 2008-01-29
The only thing I can think of is to burn the iso at even a slower speed like x4 or less and try another program to burn like [imgburn]("http://www.imgburn.com/")
and check the disk for errors (one of the options from the main menu)

---

### Post by njoubert on 2008-01-30
i tried imgburn and it made little difference. i'm fairly confident that the CDs are fine - it seems to be the kernel that can't handle the chipset. Any advice?

---

### Post by jeffus_il on 2008-01-30
From the Gigabyte site:
> Due to different Linux support condition provided by chipset vendors, please download Linux driver from chipset vendors' website or 3rd party website.[http://tw.giga-byte.com/Products/Motherboard/Products_Spec.aspx?ProductID=2535](http://tw.giga-byte.com/Products/Motherboard/Products_Spec.aspx?ProductID=2535)

From: [http://kerneltrap.org/mailarchive/linux-kernel/2007/8/26/164870](http://kerneltrap.org/mailarchive/linux-kernel/2007/8/26/164870)
> This patch, loosely based on a patch from Robert Hancock, which was in
turn based on a patch from Jesse Barnes, fixes a boot-time hang on my
shiny new PC.  The 'conflict' mentioned in the patch in my case happens
to be between mmconfig and the graphics card, but it could easily be
between any pair of devices if they are left enabled by the BIOS and
mappen in the wrong place.


Seems like you may need a later version kernel which has a problem patched. You could try "Hardy".

---

### Post by njoubert on 2008-01-31
SOLUTION:

It seems like I found a solution to my problem by combining a bunch of information. Here you go:

Distribution: Ubuntu 8.04 Alpha 3
Kernel: 2.6.24

BIOS Settings (From [http://gentoo-wiki.com/HARDWARE_Intel_G33,_Q35,_and_Q33_Chipsets](http://gentoo-wiki.com/HARDWARE_Intel_G33,_Q35,_and_Q33_Chipsets))
SATA = AHCI Native Mode
AHCI = On
processor = Native Mode

Boot Options:
acpi=off noacpi nolacpi pci=conf1

This got me into the liveCD and everything seems to work just nicely! It is installing at the moment, so I'll post a follow up soon...

---

### Post by njoubert on 2008-01-31
After installing, Ubuntu booted to the login screen, but once I logged in, the machine did not boot past the orange-colored-blank-desktop state... Apparently this is a known bug, as documented here:

[http://ph.ubuntuforums.com/showthread.php?t=665681](http://ph.ubuntuforums.com/showthread.php?t=665681)

All you have to do is kill the gnome-keyring process to boot past it.

I managed to get the current Ubuntu 7.10 (2.6.22) kernel booting to the liveCD as well using the previous config parameters. I'm installing that at the moment, so I'll report back with what my success is once that's running.

---

