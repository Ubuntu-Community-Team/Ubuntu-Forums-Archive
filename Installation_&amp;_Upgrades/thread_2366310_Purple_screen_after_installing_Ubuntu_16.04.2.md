---
title: "Purple screen after installing Ubuntu 16.04.2"
date: 2017-07-16
forum: Installation &amp; Upgrades
---

### Post by RobGoss on 2017-07-16
Hello everyone, I recently had to reinstall my system with Ubuntu 16.04.2, everything is working great except for when I restart my machine, I'm faced with a purple screen each time I restart the machine. The machine will shut down OK and I can start the machine but! when I have the machine on and try restarting it, it hangs on that purple screen and will not restart. I've been reading up on this problem and I'm thinking it has something to do with the **splash screen** and** nomodeset **I could be wrong

Thanks so much for any help on this, I hope the details below with also help trouble shoot this issue


```
00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 0e)
	Subsystem: Dell Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register
	Flags: bus master, fast devsel, latency 0
	Kernel driver in use: iosf_mbi_pci

00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0e) (prog-if 00 [VGA controller])
	Subsystem: Dell Atom Processor Z36xxx/Z37xxx Series Graphics & Display
	Flags: bus master, fast devsel, latency 0, IRQ 90
	Memory at 90000000 (32-bit, non-prefetchable) [size=4M]
	Memory at 80000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 2050 [size=8]
	[virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:13.0 SATA controller: Intel Corporation Atom Processor E3800 Series SATA AHCI Controller (rev 0e) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Atom Processor E3800 Series SATA AHCI Controller
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 88
	I/O ports at 2048 [size=8]
	I/O ports at 205c [size=4]
	I/O ports at 2040 [size=8]
	I/O ports at 2058 [size=4]
	I/O ports at 2020 [size=32]
	Memory at 90914000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:14.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI (rev 0e) (prog-if 30 [XHCI])
	Subsystem: Dell Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI
	Flags: bus master, medium devsel, latency 0, IRQ 87
	Memory at 90900000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd

00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 0e)
	Subsystem: Dell Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine
	Flags: bus master, fast devsel, latency 0, IRQ 91
	Memory at 90800000 (32-bit, non-prefetchable) [size=1M]
	Memory at 90700000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: mei_txe
	Kernel modules: mei_txe

00:1b.0 Audio device: Intel Corporation Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller (rev 0e)
	Subsystem: Dell Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 92
	Memory at 90910000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 1 (rev 0e) (prog-if 00 [Normal decode])
	Flags: fast devsel, IRQ 18
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 3 (rev 0e) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: 90600000-906fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 4 (rev 0e) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 90500000-905fffff
	Prefetchable memory behind bridge: 0000000090400000-00000000904fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 0e)
	Subsystem: Dell Atom Processor Z36xxx/Z37xxx Series Power Control Unit
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich

00:1f.3 SMBus: Intel Corporation Atom Processor E3800 Series SMBus Controller (rev 0e)
	Subsystem: Dell Atom Processor E3800 Series SMBus Controller
	Flags: medium devsel, IRQ 10
	Memory at 90915000 (32-bit, non-prefetchable) [size=32]
	I/O ports at 2000 [size=32]
	Capabilities: <access denied>
	Kernel modules: i2c_i801

02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
	Subsystem: Dell QCA9565 / AR9565 Wireless Network Adapter
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 90600000 (64-bit, non-prefetchable) [size=512K]
	Expansion ROM at 90680000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
	Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
	Flags: bus master, fast devsel, latency 0, IRQ 89
	I/O ports at 1000 [size=256]
	Memory at 90500000 (64-bit, non-prefetchable) [size=4K]
	Memory at 90400000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

```

---

### Post by Dennis N on 2017-07-16
Maybe it's waiting for one of those "stop jobs" to finish. If you let it alone for 2 minutes, does it reboot anyway? I used to see the "stop job" problem with 16.04, but not for a while. Also, you can press ESC when you have the purple screen to break to console output. You may see what it is up to that is slowing things up.

---

### Post by RobGoss on 2017-07-16
Hi Dennis, well it also hangs when I restart it and displays the Dell logo and sometimes the purple screen. I'm not sure what's going on

**EDIT:** So after seeing the Dell logo just hanging I decided it may be something with the BIOS, so I changed the BIOS from UEFI to Legacy and it seems to be booting OK now, I'm not sure why making this change would have affected my boot up

---

