---
title: "Networking problems on fresh 6.10 install"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by GEnX20 on 2007-01-15
Hi there,

I've just installed ubuntu on a factory new box. It's equipped with an ASUS P5L-VM 1394 motherboard. I have had no trouble installing the system, but it seems theinstaller did not configure networking. Well maybe because there is a problem recognising my interface, because this is what lspci-v gives me:
```
00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub (rev 02)
	Subsystem: ASUSTeK Computer Inc. Unknown device 817a
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation 945G/GZ Express Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
	Subsystem: ASUSTeK Computer Inc. Unknown device 817a
	Flags: bus master, fast devsel, latency 0, IRQ 169
	Memory at cfc80000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 8800 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at cfd80000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [90] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 2

00:02.1 Display controller: Intel Corporation 945G/GZ Express Integrated Graphics Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Unknown device 817a
	Flags: bus master, fast devsel, latency 0
	Memory at cfd00000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8249
	Flags: bus master, fast devsel, latency 0, IRQ 225
	Memory at cfdf8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
	Capabilities: [90] #0d [0000]
	Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: cff00000-cfffffff
	Capabilities: [40] Express Root Port (Slot-) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
	Capabilities: [90] #0d [0000]
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 217
	I/O ports at 9000 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 177
	I/O ports at 9400 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 209
	I/O ports at 9800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 225
	I/O ports at a000 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 217
	Memory at cfdffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: cfe00000-cfefffff
	Capabilities: [50] #0d [0000]

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8179
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 209
	I/O ports at <unassigned>
	I/O ports at <unassigned>
	I/O ports at <unassigned>
	I/O ports at <unassigned>
	I/O ports at ffa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device 2601
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 177
	I/O ports at b800 [size=8]
	I/O ports at b400 [size=4]
	I/O ports at b000 [size=8]
	I/O ports at a800 [size=4]
	I/O ports at a400 [size=16]
	Capabilities: [70] Power Management version 2

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8179
	Flags: medium devsel
	I/O ports at 0400 [size=32]

01:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81fe
	Flags: bus master, medium devsel, latency 64, IRQ 233
	Memory at cfeff800 (32-bit, non-prefetchable) [size=2K]
	I/O ports at c800 [size=128]
	Capabilities: [50] Power Management version 2

02:00.0 Ethernet controller: Unknown device 1969:1048 (rev b0)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8226
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at cffc0000 (64-bit, non-prefetchable) [size=256K]
	Expansion ROM at cffa0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
	Capabilities: [58] Express Endpoint IRQ 0


```

and this is the output from ifconfig:

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28192 (27.5 KiB)  TX bytes:28192 (27.5 KiB)


```

and this is what i get from cat /etc/networking/interfaces

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


```

Any idea what may cause this problem?
Thanks a lot for your advice,
Gregor

---

### Post by acacs on 2007-03-26
The module to use with this interface is the atl1. See if it's already loaded, and if it's not, load it.

To see if it's already loaded:

```
 lsmod | grep atl1 
```

To load it:

```
 sudo modprobe atl1 
```

---

### Post by lukemh on 2007-04-10
i have the same motherboard and the same networking problem... i tried sudo modprobe atl1 and it sayd FATAL: module atl1 not found

any more ideas?

---

