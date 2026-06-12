---
title: "Serial mouse&amp;keyboard working irregular from 10.04 on"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by walterwerner on 2010-10-09
I have Ubuntu 9.10, both server and desktop working really fine on my 
ASUS P4S800D R1011 b004 Motherboard and AMI-Bios V02.54. I am using serial keyboard and serial mouse, everything works fine. Here is the rest of the hardware (output from lspci)
> 1:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 655 Host (rev 50)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:09.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
I have tried installing (fresh or upgrade, no difference) 10.04, both server and  desktop, but with 10.04 the serial keyboard does not behave properly, and the mouse also does funny things before it stucks completely. 
Is there a way to "add" the 9.10 (and before) performance of the serial devices to 10.4 and 10.10?

Regards Walter

---

