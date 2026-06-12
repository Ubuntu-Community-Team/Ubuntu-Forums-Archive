---
title: "Xubuntu 14.04 upgrade to 14.10 GeForce GTX 260 safe?"
date: 2015-03-17
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2015-03-17
Hi,

I tried for a bit to install Xubuntu 14.10 on old i7 920.  I gave up and put 14.04 on with very little problem, and it's up and running.

I'd rather have bleeding edge software, so I'm wondering if anyone has tried a dist upgrade successfully with my video hardware?

I don't want to fight this.  I need this box for software development, but would rather reinstall with what I have now rather than get everything set up and then have to reinstall later.  **And MUCH more I would rather keep it on 14.04 rather than have to fight with it.**

Thanks.

```

lspci -vnn   # I just cut my video card for details.

[COLOR=#4C2F2D][FONT=Courier]02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT200 [GeForce GTX 260] [10de:05e2] (rev a1) (prog-if 00 [VGA controller])[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Subsystem: Device [196e:064b][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Flags: bus master, fast devsel, latency 0, IRQ 71[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Memory at f2000000 (32-bit, non-prefetchable) [size=16M][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Memory at c0000000 (64-bit, prefetchable) [size=256M][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Memory at f0000000 (64-bit, non-prefetchable) [size=32M][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    I/O ports at ac00 [size=128][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Expansion ROM at f3c80000 [disabled] [size=512K][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Capabilities: [60] Power Management version 3[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Capabilities: [78] Express Endpoint, MSI 00[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Capabilities: [100] Virtual Channel[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Capabilities: [128] Power Budgeting <?>[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Kernel driver in use: nouveau[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]
[/FONT][/COLOR]

```

```

lspci -nn

[COLOR=#4C2F2D][FONT=Courier]00:00.0 Host bridge [0600]: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port [8086:3405] (rev 12)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:01.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 [8086:3408] (rev 12)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:03.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 [8086:340a] (rev 12)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:07.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 [8086:340e] (rev 12)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:14.0 PIC [0800]: Intel Corporation 7500/5520/5500/X58 I/O Hub System Management Registers [8086:342e] (rev 12)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:14.1 PIC [0800]: Intel Corporation 7500/5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers [8086:3422] (rev 12)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:14.2 PIC [0800]: Intel Corporation 7500/5520/5500/X58 I/O Hub Control Status and RAS Registers [8086:3423] (rev 12)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:14.3 PIC [0800]: Intel Corporation 7500/5520/5500/X58 I/O Hub Throttle Registers [8086:3438] (rev 12)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:1a.0 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:1a.1 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:1a.2 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:1a.7 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:1c.2 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3 [8086:3a44][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:1c.3 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4 [8086:3a46][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 [8086:3a48][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:1d.0 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:1d.1 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:1d.2 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:1d.7 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:1f.2 SATA controller [0106]: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller [8086:3a22][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT200 [GeForce GTX 260] [10de:05e2] (rev a1)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]04:00.0 SATA controller [0106]: JMicron Technology Corp. JMB363 SATA/IDE Controller [197b:2363] (rev 03)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]04:00.1 IDE interface [0101]: JMicron Technology Corp. JMB363 SATA/IDE Controller [197b:2363] (rev 03)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]05:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6315 Series Firewire Controller [1106:3403][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]08:00.0 Multimedia audio controller [0401]: Creative Labs SB X-Fi [1102:0005][/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:00.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers [8086:2c41] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:00.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder [8086:2c01] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:02.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 QPI Link 0 [8086:2c10] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:02.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 [8086:2c11] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:03.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller [8086:2c18] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:03.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder [8086:2c19] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:03.4 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers [8086:2c1c] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:04.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers [8086:2c20] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:04.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers [8086:2c21] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:04.2 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers [8086:2c22] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:04.3 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers [8086:2c23] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:05.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers [8086:2c28] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:05.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers [8086:2c29] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:05.2 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers [8086:2c2a] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:05.3 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers [8086:2c2b] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:06.0 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers [8086:2c30] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:06.1 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers [8086:2c31] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:06.2 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers [8086:2c32] (rev 05)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]ff:06.3 Host bridge [0600]: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers [8086:2c33] (rev 05)[/FONT][/COLOR]

```

---

