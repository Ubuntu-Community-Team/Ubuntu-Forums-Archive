---
title: "Any successful 8.04 sata installs?"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by SomalianViking on 2008-04-26
I notice a lot of people having trouble installing or upgrading to 8.04. A lot of the problems as well as my own dealing with not detecting SATA drives. 

Has anybody successfully installed 8.04 on their computer on a SATA drive? If so what chipset does your sata devices use; or did you do anything special during the install to detect your drive(s)?

---

### Post by uboel on 2008-04-26
I yesterday, I installed successfully UBUNTU 8.04 on my SATA HD.
My motherboard is an ASUS P5W DH Deluxe for which I have the following SATA controllers:

Intel ICH7R South Bridge:
* 1 x UltraDMA 100/66/33
* 3 x Serial ATA 3.0Gb/s with Intel® Matrix Storage Technology with RAID 0, 1, 5 support
Jmicron JMB363 controller
* 1 x UltraDMA 133/100/66
* 1x Serial SATA 3.0Gb/s
* 1x External Serial ATA 3.0Gb/s (ASUS SATA-on-the-Go)
* Support SATA RAID 0, 1 and JBOD (by 1x External SATA & 1x Internal SATA)
Silicon Image 4723 Hardware RAID controller (ASUS EZ-Backup)
* 2 x Serial ATA 3.0Gb/s with RAID 0, 1 support
* Support RAID 10 cross Intel® ICH7R and Silicon Image 4723 controller

The JMicron controller is disabled and my installation HD is connected to the Intel one.
I did nothing special, it worked on the first attempt.

Kind regards,

Ulric

---

### Post by Alienwarem9750 on 2008-05-06
So you disabled the SATA Raid in order to install 8.04

That seems like the easiest option

---

### Post by Aearenda on 2008-05-06
Mine works fine with the BIOS set to RAID mode - Dell 530. lspci shows ```
RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
```
The Dell 530 problem has been that Hardy won't work unless it IS in RAID mode.

---

### Post by Alienwarem9750 on 2008-05-06
> **Aearenda said:**
> Mine works fine with the BIOS set to RAID mode - Dell 530. lspci shows ```
RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
```
The Dell 530 problem has been that Hardy won't work unless it IS in RAID mode.


Does that laptop use a SATA Raid ?  if so  how did you set it up?

---

### Post by Aearenda on 2008-05-06
It's actually a desktop. For Hardy we have to set the SATA mode to RAID in the BIOS settings, but that just changes the way the BIOS presents the drives to the kernel; it doesn't mean we are actually using RAID.

---

