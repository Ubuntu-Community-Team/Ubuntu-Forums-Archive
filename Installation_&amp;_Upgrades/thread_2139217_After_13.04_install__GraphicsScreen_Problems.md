---
title: "After 13.04 install : Graphics/Screen Problems"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by iSpud on 2013-04-26
I upgraded from 12.10 to 13.04. Now on boot up I either get a black screen with a rainbow of various random pixels or repeating patterns. Does this relate to the sticky post above? Help? :confused:

---

### Post by kc1di on 2013-04-26
Hi iSpud, 

Not having seen the sticky you mentioned I'm not sure of it relationship. but it's most likey to be a video card problem.
could you go to a teminal and type the following command and post the results here please.
```
lspci
```

---

### Post by iSpud on 2013-04-26
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller

---

### Post by iSpud on 2013-04-27
I've also tried booting from a 13.04 usb install drive, and it shows the initial keyboard/accessibility logo but then the graphics go haywire.

---

### Post by iSpud on 2013-04-29
Anyone have any advice? I did submit a bug.

---

