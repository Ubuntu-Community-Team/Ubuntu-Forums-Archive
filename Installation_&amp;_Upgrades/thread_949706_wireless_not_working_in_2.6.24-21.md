---
title: "wireless not working in 2.6.24-21"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by dullard on 2008-10-16
Apologies if there's already a thread for this problem in Ubuntu. I searched but didn't find.

Update manager installed a load of stuff today and after rebooting I wasn't able to use my wireless connection. Reverting to the previous kernel works okay but here's a couple of things I noticed before switching back:

System>Administration>Network - Under the Connections tab,the 'wireless connection' setting was missing. I was left with only the 'wired' and 'Point to point' options.

System>Administration>Hardware Drivers - Suddenly had a new component listed, called 'Wl'.

Anybody else getting this? And since the former kernel works nicely, should I be scared of every update in future?

---

### Post by StOoZ on 2008-10-16
what the output of
> lspci -v

and also , did the wirelss worked out-of-the-box when you first installed ubuntu

---

### Post by dullard on 2008-10-16
I've been using wireless since Gutsy Gibbon and then Hardy Heron without a hitch until today.

Here's the output of  lspci -v using the kernel I've rolled back to. I'm assuming the new kernel will produce the same result but will boot into that one and run that command if necessary. 

```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
	Subsystem: Dell Unknown device 01fd
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fe900000-feafffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Memory behind bridge: fe800000-fe8fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
	Capabilities: <access denied>

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe600000-fe7fffff
	Prefetchable memory behind bridge: 00000000f0100000-00000000f03fffff
	Capabilities: <access denied>

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Unknown device 01fd
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 6eb0 [size=8]
	I/O ports at 6eb8 [size=4]
	I/O ports at 6ec0 [size=8]
	I/O ports at 6ec8 [size=4]
	I/O ports at 6ee0 [size=16]
	Memory at 88000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 01fd
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at ffb00000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 01fd
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at ffb01000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 01fd
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at ffb02000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 01fd
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at ffb03000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 01fd
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at ffb04000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 01fd
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
	Memory at ffa80000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
	Subsystem: Dell Unknown device 01fd
	Flags: 66MHz, medium devsel
	I/O ports at 10c0 [size=16]
	Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Unknown device 01fd
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
	Subsystem: Dell Unknown device 01fd
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: Dell Unknown device 01fd
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	Memory behind bridge: fe500000-fe5fffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series] (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 01fd
	Flags: bus master, fast devsel, latency 64, IRQ 19
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at ee00 [size=256]
	Memory at fea00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Unknown device 01fd
	Flags: bus master, fast devsel, latency 64, IRQ 21
	Memory at fe5fe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 01fd
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at fe5fd800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
	Subsystem: Dell Unknown device 01fd
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at fe5fd500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Dell Unknown device 01fd
	Flags: bus master, medium devsel, latency 64, IRQ 7
	Memory at fe5fd600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
	Subsystem: Dell Unknown device 01fd
	Flags: bus master, medium devsel, latency 64, IRQ 7
	Memory at fe5fd700 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
	Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
	Memory at f0000000 (64-bit, prefetchable) [size=1M]
	Capabilities: <access denied>

```

---

### Post by dullard on 2008-10-17
*bump*

Not too worried about having to use 2.6.24-19 for now, but is it likely I'll have to avoid every kernel upgrade from -21 onwards?

I'm still learning the ropes, like :-)

---

### Post by dpologea on 2008-10-18
I confirm that I have exactly the same problem on my laptop Dell D830 with the chipset Intel PRO/Wireless 3945ABG.

I am running Hardy Heron with kernel 2.6.24-19 and I have installed the updates to the kernel 2.6.24-21. After this update I am not able to use wireless anymore.

I am using the old 2.6.24-19 just to be able to use the wireless.
2.6.24-21 needs a patch with respect to this problem.

---

### Post by dpologea on 2008-10-27
It seems the problem is with linux-backports-modules-2.6.24-21-generic. Uninstalling it, solves the problem. As a side effect my driver for the X.Org X server has misconfigured. What is the connection between these two I don't know. I have solved the problem reinstalling xserver-xorg-video-nv module (I have a NVidia card). Obviously, if there is something in linux-backports-modules-2.6.24-21-generic that you really need there is still an issue. For instance, the wireless LED light is always off without the backport module (I have a laptop Dell D830).

---

### Post by Yiftos on 2008-10-27
> **dullard said:**
> *bump*

Not too worried about having to use 2.6.24-19 for now, but is it likely I'll have to avoid every kernel upgrade from -21 onwards?

I'm still learning the ropes, like :-)

I just upgraded to Hardy Heron from Gutsy Gibbon and now my wireless (Atheros)does not work but with hard it was great. Also vpnc only works with command line.

Since, I am a newby, how do you *BUMP* to a previous kernel? Or roll back to Gutsy.

---

