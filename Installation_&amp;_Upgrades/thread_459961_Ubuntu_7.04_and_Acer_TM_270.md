---
title: "Ubuntu 7.04 and Acer TM 270"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by mysteron on 2007-05-31
Hi.

I've got an old Acer TravelMate 270 and whatever I try, I cannot get Ubuntu 7.04 to boot on this machine. This is a new installation of 7.04. Never tried Ubuntu before so I thought I'd give it a go. Anwyways, all Ubuntu does is take a long time right after the splash screen appears (not even the load bar starts animating), and then it drops me into an initramfs prompt. As I mentioned, this is a new installation. Novell/Suse Linux 10.0 have worked flawlessly on this machine. Help will be greatly appreciated :)


Thx,
/mysteron

---

### Post by apunc1 on 2007-05-31
what are the specs of the machine?
give the alternate cd a try. i assume you're trying to boot from the live cd.

---

### Post by mysteron on 2007-06-01
> **apunc1 said:**
> what are the specs of the machine?
give the alternate cd a try. i assume you're trying to boot from the live cd.

Thank you for you reply :) The 7.04 livecd boots without any problems. It is when the machine tries to boot ubuntu after the installation procedure is done, that's when ubuntu takes an age and finally I'm dumped to a initramfs prompt.

The specs of the machine are:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:09.0 CardBus bridge: ENE Technology Inc CB1420 Cardbus Controller (rev 01)
00:09.1 CardBus bridge: ENE Technology Inc CB1420 Cardbus Controller (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

model name      : Mobile Intel(R) Pentium(R) 4 - M CPU 1.70GHz

A total of 512 mb memory (the VGA adapter uses some of that memory though).


thx,
/mysteron

---

### Post by sedition on 2007-06-09
Ran into the same type of problem on my Libretto 110 after installing the server (text-only) version. Someone found a temporary fix in a bug report that you can check out in this thread:
([http://ubuntuforums.org/showthread.php?t=452788](http://ubuntuforums.org/showthread.php?t=452788)), but it still has to be manually typed in every boot.

---

