---
title: "No sound after installation"
date: 2012-12-12
forum: Installation &amp; Upgrades
---

### Post by satimis on 2012-12-12
Hi all

Ubuntu 12.04 desktop 64bit
Motherboard - ASUS M5A97 R2.0
Output - HDMI

Downloand
Unix (Linux)
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

Linux driver (3.0) - LinuxPkg_5.17rc13.tar.bz2

extract to:
/Downloads/realtek-linux-audiopack-5.17

$ ls Downloads/realtek-linux-audiopack-5.17/```

alsa-driver-1.0.25-5.17rc13.tar.bz2  Readme.txt
install                              test.wav.bz2
Linux Audio Installation guide.pdf   version

```

cd /Downloads/realtek-linux-audiopack-5.17
$ sudo ./install

Installation went through without complaint

reboot PC

System Settings -> Sound -> Outpu
HDMI is not there

Please help.  TIA

Edit:
$ cat /proc/asound/card0/codec* | grep Codec```

Codec: Realtek ALC887-VD

```

$ cat /proc/asound/cards ```

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfeb00000 irq 16
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfea40000 irq 90

```

B.R.
satimis

---

### Post by vasilisc on 2012-12-12
please give me
```
sudo lspci -vnnk
```

---

### Post by satimis on 2012-12-12
> **vasilisc said:**
> please give me
```
sudo lspci -vnnk
```


$ sudo lspci -vnnk
```

00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (external gfx0 port B) [1002:5a14] (rev 02)
	Subsystem: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (external gfx0 port B) [1002:5a14]
	Flags: fast devsel
	Capabilities: [f0] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [c4] HyperTransport: Slave or Primary Interface
	Capabilities: [40] HyperTransport: Retry Mode
	Capabilities: [54] HyperTransport: UnitID Clumping
	Capabilities: [9c] HyperTransport: #1a
	Capabilities: [70] MSI: Enable- Count=1/4 Maskable- 64bit-

00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port B) [1002:5a16] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fea00000-feafffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] nee ATI Device [1002:5a14]
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [190] Access Control Services
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port D) [1002:5a18] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d00fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] nee ATI Device [1002:5a14]
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [190] Access Control Services
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port E) [1002:5a19] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fe900000-fe9fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] nee ATI Device [1002:5a14]
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [190] Access Control Services
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port G) [1002:5a1b] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: fe800000-fe8fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] nee ATI Device [1002:5a14]
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [190] Access Control Services
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] (rev 40) (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. Device [1043:84dd]
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
	I/O ports at f040 [size=8]
	I/O ports at f030 [size=4]
	I/O ports at f020 [size=8]
	I/O ports at f010 [size=4]
	I/O ports at f000 [size=16]
	Memory at feb0b000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [70] SATA HBA v1.0
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: ahci

00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
	Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at feb0a000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
	Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	Memory at feb09000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
	Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 20
	Memory at feb08000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
	Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 21
	Memory at feb07000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 42)
	Subsystem: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385]
	Flags: 66MHz, medium devsel
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4

00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8444]
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at feb00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
	Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384] (rev 40) (prog-if 01 [Subtractive decode])
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=64

00:14.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399] (prog-if 10 [OHCI])
	Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at feb06000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:16.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
	Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 22
	Memory at feb05000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:16.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
	Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 23
	Memory at feb04000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 0 [1022:1600]
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 1 [1022:1601]
	Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 2 [1022:1602]
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 3 [1022:1603]
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 4 [1022:1604]
	Flags: fast devsel
	Kernel driver in use: fam15h_power
	Kernel modules: fam15h_power

00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 5 [1022:1605]
	Flags: fast devsel

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Caicos [Radeon HD 6450] [1002:6779] (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device [1043:03da]
	Flags: bus master, fast devsel, latency 0, IRQ 89
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at fea20000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at e000 [size=256]
	Expansion ROM at fea00000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting
	Kernel driver in use: radeon
	Kernel modules: radeon

01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Caicos HDMI Audio [Radeon HD 6400 Series] [1002:aa98]
	Subsystem: ASUSTeK Computer Inc. Device [1043:aa98]
	Flags: bus master, fast devsel, latency 0, IRQ 90
	Memory at fea40000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8505]
	Flags: bus master, fast devsel, latency 0, IRQ 88
	I/O ports at d000 [size=256]
	Memory at d0004000 (64-bit, prefetchable) [size=4K]
	Memory at d0000000 (64-bit, prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
	Capabilities: [d0] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 24-00-00-00-68-4c-e0-00
	Kernel driver in use: r8169
	Kernel modules: r8169

03:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042] (prog-if 30 [XHCI])
	Subsystem: ASUSTeK Computer Inc. Device [1043:8488]
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at fe900000 (64-bit, non-prefetchable) [size=32K]
	Capabilities: [50] MSI: Enable- Count=1/8 Maskable- 64bit+
	Capabilities: [68] MSI-X: Enable+ Count=8 Masked-
	Capabilities: [78] Power Management version 3
	Capabilities: [80] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Kernel driver in use: xhci_hcd

04:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042] (prog-if 30 [XHCI])
	Subsystem: ASUSTeK Computer Inc. Device [1043:8488]
	Flags: bus master, fast devsel, latency 0, IRQ 50
	Memory at fe800000 (64-bit, non-prefetchable) [size=32K]
	Capabilities: [50] MSI: Enable- Count=1/8 Maskable- 64bit+
	Capabilities: [68] MSI-X: Enable+ Count=8 Masked-
	Capabilities: [78] Power Management version 3
	Capabilities: [80] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Kernel driver in use: xhci_hcd

```

Thanks

B.R.
satimis

---

