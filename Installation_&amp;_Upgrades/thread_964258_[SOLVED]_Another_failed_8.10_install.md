---
title: "[SOLVED] Another failed 8.10 install"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by achelis on 2008-10-30
Hi

Just tried to install Kubuntu 8.10 on my system. I burned the live cd (i386) and tried to boot. First I tried to install directly, but this gave a black screen and sort of froze - afterwards I tried to boot into Kubuntu, but that kind of crashed as well. 

I was able to log in to tty1, but I'm not really proficient enough to get anything useful out of that.

I checked the CD for defects and the report said nothing is wrong.

I've run Kubuntu 8.04 on the machine without problems and hardware hasn't changed.

Currently I have a dual-boot setup with Windows XP and Ubuntu 8.04 which works without problems.

Hardware (output from lspci in Ubuntu)
```

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)

```

I have two harddrives. The primary drive has an unformatted partition where I intended to install Kubuntu to try out KDE4.

---

### Post by lemming465 on 2008-10-31
Unfortunately, the X support for legacy ATI and legacy nvidia chips regressed a bit between 8.04 and 8.10.  You may want to stick to 8.04 for a while longer, until that gets sorted out better.  Booting in safe mode (with the "vesa" driver) might work, though you might not get the same resolution and performance as previously.

---

### Post by achelis on 2008-11-01
Thanks for the info. Guess I'll have to wait it out. Do you think a new version of the LiveCD will be released?

Computers age quickly these days though :/ - 1 year and your graphics card is already legacy *sigh*

Edit: Just tried to boot the Live CD in save mode and I can confirm it works. Installation failed though (unable to read from CD or something similar) - apparently I need to burn the CD at a slower speed.

---

### Post by jfollmann on 2008-11-01
> **lemming465 said:**
> Unfortunately, the X support for legacy ATI and legacy nvidia chips regressed a bit between 8.04 and 8.10.  You may want to stick to 8.04 for a while longer, until that gets sorted out better.  Booting in safe mode (with the "vesa" driver) might work, though you might not get the same resolution and performance as previously.


Wait, an 8800GT is "legacy?" Seriously?

---

### Post by achelis on 2008-11-02
I'm not sure. Once installed I was able to choose the restricted NVidia drivers as usual and everything works like it should. Think it may have been an issue with burning the CD at maximum speed at first.

---

