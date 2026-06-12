---
title: "wubi install messes up windows network connection"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by sydd1 on 2010-05-17
Hi

I just installed 10.04 64 bit to a windows 7 64 bit.
After the install wubi works fine (except it hangs for like 1 minute saying Try hd(0,0) NTFS5: no wubildr), but windows 7 cant connect to the internet anymore. if i run ipconfig, it lests my ethernet adapter, but says that no network connection avaiable, the troubleshooter advises to plug in my ethernet cable.
(it is plugged in, the net from ubuntu works fine.)

Heres the output from lspci, dunno if helps:
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

Anyone has this problem?

---

### Post by Saya on 2010-08-08
I have the same problem. Windows 7 x64, Wubi 10.04 x64, onboard Realtek RTL8111D on a Gigabyte UD-3.
I have tried pretty much everything excluding reformatting my harddrive.

---

