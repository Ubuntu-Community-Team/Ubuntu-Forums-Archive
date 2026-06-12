---
title: "Boot repair issue"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by icyisaac100 on 2012-12-19
After installing legacy conky, the computer booted with a purple screen. I used boot repair and it fixed it on the live cd, but the next time, it went back to the purple screen. I have done this twice with  the same result. 
 
I also had issues when I installed the computer- but was fixed by the live cd.

Might be my graphics - do you agree?  
After typing sudo lspci |more

> 00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated
 Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio C
ontroller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 0
1)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 0
1)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #
1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #
2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #
3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #
4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller 
(rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bri
dge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (re
v 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE m
ode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E P
CI Express Fast Ethernet controller (rev 05)


---

### Post by icyisaac100 on 2012-12-19
It may have been something apart from conky, but that was the last thing I installed

---

