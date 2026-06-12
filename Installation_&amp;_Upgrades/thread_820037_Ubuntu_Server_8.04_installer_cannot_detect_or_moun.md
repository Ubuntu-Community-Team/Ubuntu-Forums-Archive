---
title: "Ubuntu Server 8.04 installer cannot detect or mount CD-ROM"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by mwjones on 2008-06-05
I am attempting to install Ubuntu Server 8.04 and encountering the following error message:

> [!!] Detect and mount CD-ROM

Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not in the drive. If so you can insert it and try again.

Try again to mount the CD-ROM? <Yes> <No>

The same error occurs when I attempt to check the CD for defects. Motherboard is ABIT AI7 with 2 SATA and 2 PATA slots. Hard drive is 750GB SATA, and I have tried with both SATA and PATA DVD+/-RW drives. The Kubuntu 8.04 LiveCD loads fine, and installs fine once the OS is loaded into memory. I have tried several different boot options from searching and none work. There are similar bugs, but with different circumstances (such as external firewire CD-ROM drive as opposed to internal ATA).

Please let me know what additional pieces of information are required to troubleshoot this problem.

Cheers,
mwjones

---

### Post by Pumalite on 2008-06-05
Edit your boot line and add all_generic_ide at the end.
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by mwjones on 2008-06-06
Unfortunately **all_generic_ide** does not fix the problem.  Currently I have the SATA DVD+/-RW drive in, but have tried it with both.  Additionally, since Ubuntu is not yet installed, F6 is required to edit the boot parameters (as opposed to e in GRUB).

---

### Post by mwjones on 2008-06-07
I've tried some additional items such as burning to different discs at different speeds, changing the mode in the BIOS (Auto, Enhanced, Combined, SATA Only), etc.  A bug has been opened for this issue [https://bugs.launchpad.net/ubuntu/+bug/237800](https://bugs.launchpad.net/ubuntu/+bug/237800)

Please post any other suggestions.

---

### Post by mwjones on 2008-06-13
Just an update on my end:  I have moved on to just using Kubuntu 8.04.  For further information on this issue, I guess just follow the bug report.  Good luck!

---

### Post by alphadogg on 2008-09-17
Having a similar issue trying to install Ubuntu Server 8.04. Mobo is an ECS P43T-A2, DVD drive is a Lite-On 16D3S (a SATA DVD-ROM).

The ironic thing is the installer boots just fine from the same drive it apparently can see during install... :confused:

---

### Post by jblevins on 2008-10-21
Exact problem here.  Looking for a solution.  Not really appreciating the irony of being unable to detect the cdrom (DVDdrive) doing the install....

MOBO P45 NEO3
sata connected dvd drive
ide connected hdd
(2) sata connected HDD drives.

---

### Post by Pumalite on 2008-10-21
I've heard changing ACHI to Raid sometimes works

---

### Post by wookinpanub on 2008-12-01
I'm having similar issues and have tried EVERYTHING I can find on these posts.

First off, here is my hardware:

ABit F190-HD Motherboard (Phoenix BIOS v6.00 PG)
Intel Q6600 Core 2-Quad CPU @ 2.4 GHz
(2) Corsair CM2X1024-6400 RAM (5-5-5-12 | 800 mHz | 1.90v)
(2) LG GSA-H62N DVD-RW +/- SATA Drives
Seagate ST3500630AS SATA 500GB HDD
Seagate ST3250620A IDE 250GB HDD
Belkin F8T001 USB Bluetooth Dongle
ViewSonic 22" VX2245wm ViewDock LCD Widescreen Monitor (Connected via HDMI-to-DVI Cable -- Motherboard output HDMI)

Second, I have attempted to install from a bootable ISO download of 8.10 Studio for both x86 and amd64, both with same results. After successfully selecting keyboard and language it cannot mount/find/see CD-ROM (even though it booted on it from a reboot).

Third, I downloaded 9.04 Live CD and attempted to run from CD-ROM to see if newer version would work. Logo appears with progress bar, after several minutes I get a "initramfs" prompt.  No dice there either.

I read a few other posts and tried the "ide=nodma", "all_generic_ide", and "irqpoll" tricks with no success at all.  No luck with switching to RAID either, Legacy IDE was the only successful way to boot, otherwise my BIOS looks for a RAID setup and never finds it and locks up.

Also, I tried re-installing my NEC IDE DVD-RW +/- to see if it was SATA related. No changes from above. I disconnected all SATA devices and USB devices (except for the mouse) and no changes from above.

Any ideas? I'm a Linux newbie, so be gentle.

---

