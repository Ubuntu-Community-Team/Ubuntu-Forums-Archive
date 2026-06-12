---
title: "Installing HP Printer/WiFi Capabilities"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by evolushun on 2007-10-01
OK.  So far so good.  I appreciate all the help I have had and this community rocks.  Now, I have a few questions regarding my printer and WiFi.  First of all, I have an HP PSC 1315xi All In One printer and want to know how to install it.  Secondly, I have a built-in wireless card and would like to be able to access it.  I haven't tried so I am not sure if it is or isn't installed so I guess I want to know if it installs automatically?  I don't have a router that works and driving somewhere to check WiFi doesn't seem necessary.  Thanks in advance!

---

### Post by sstusick on 2007-10-01
Plug in the printer, go to system > Administration > Printing and Add Printer.

---

### Post by evolushun on 2007-10-01
> **sstusick said:**
> Plug in the printer, go to system > Administration > Printing and Add Printer.

OMG...too easy!  Is there anything this OS doesn't do well?

---

### Post by sstusick on 2007-10-01
I can't think of anything :-D

---

### Post by evolushun on 2007-10-01
Now, would my wireless card automatically install or is there a way to check if it has found it?

---

### Post by sstusick on 2007-10-01
Try > lspci in the terminal.

---

### Post by evolushun on 2007-10-01
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

---

