---
title: "Sound Problem"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by chantaspell on 2010-09-23
Hi, hope this is the right forum.
 
Just installed ubuntu on my netbook: Toshiba NB200. It is a dual boot with XP, but since I did that I have no sound in either ubuntu or XP! I do get normal sound through headphones in both, but nothing through netbook speakers.
 
Any ideas?
 
Many Thanks
 
Hmmm, I should add what I have already tried:
 
Checked the volume controls on all apps I can find in both OS.
 
Updated the Driver in xp
 
Updated chipset driver in XP

aplay -l in terminal gets me:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

thomas@NB200:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
	Subsystem: Toshiba America Info Systems Device ff60
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff60
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at f0200000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff60
	Flags: bus master, fast devsel, latency 0
	Memory at f0080000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff6e
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 80000000-801fffff
	Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f0100000-f01fffff
	Prefetchable memory behind bridge: 0000000080400000-00000000805fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 80600000-809fffff
	Prefetchable memory behind bridge: 00000000f0500000-00000000f05fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: 80a00000-80bfffff
	Prefetchable memory behind bridge: 0000000080c00000-0000000080dfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff60
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff60
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff60
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff60
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff60
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0444000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Toshiba America Info Systems Device ff60
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Device ff60
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Toshiba America Info Systems Device ff60
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 18c8 [size=8]
	I/O ports at 18c0 [size=4]
	I/O ports at 18a8 [size=8]
	I/O ports at 180c [size=4]
	I/O ports at 18b0 [size=16]
	Memory at f0444400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff60
	Flags: medium devsel, IRQ 10
	I/O ports at 18e0 [size=32]
	Kernel modules: i2c-i801

03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Accton Technology Corporation Device e811
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff60
	Flags: bus master, fast devsel, latency 0, IRQ 28
	I/O ports at 2000 [size=256]
	Memory at f0510000 (64-bit, prefetchable) [size=4K]
	Memory at f0500000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at f0520000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

And that is as far as I have got.

---

### Post by lkjoel on 2010-09-24
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by chantaspell on 2010-09-26
This was found to be caused by a hardware problem.

---

