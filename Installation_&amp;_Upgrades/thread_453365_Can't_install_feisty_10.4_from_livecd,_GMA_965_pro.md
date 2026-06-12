---
title: "Can't install feisty 10.4 from livecd, GMA 965 problem"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by WiNeOS on 2007-05-24
I'm trying to install ubuntu feisty in my laptop without luck.

First problem comes from my sata drive but I solved it with *modprobe piix*.
Here my solution
[http://ubuntuforums.org/showthread.php?t=415009&page=14](http://ubuntuforums.org/showthread.php?t=415009&page=14)

But Now, the liveCD vesa driver can't found any mode for my integrated intel GMA 965 (X3000) videocard. (the same thing with ubuntu edgy)

I tried to use the i810 driver but don't work.
I tried to install xserver-xorg-video-intel too, but apt-get can't find it in the repos. I solved it installing ssh and connecting from another computer, then i update sources.list from another ubuntu laptop (treviño repos I think).

intel deb pack version: 2:1.9.94-1
i810 deb pack version: 2:1.7.4-0u

Any idea? 

Greetz

---

### Post by WiNeOS on 2007-05-24
I installed ubuntu using *alternative * cd and using the text mode installation but the problem with the video detection continues.

My laptop motherboard uses the 965 Chipset and has an integrated Intel X3000 128MB GMA PCI-e video card. It is said to be supported by the i810 video driver. I have installed that and set it as the driver in xorg.conf.

When I try to start X I get the following messages: 
> (WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(EE) No devices detected.

Later, I installed xserver-xorg-video-intel 2:1.9.94-1ubuntu3, but again xorg crashed:
> (EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too slow?
...
(EE) intel(0): Couldn't allocate video memory

My lspci -v:
> 00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
	Subsystem: Elitegroup Computer Systems Unknown device 9037
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
	Subsystem: Elitegroup Computer Systems Unknown device 9037
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at fc000000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 3

00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
	Subsystem: Elitegroup Computer Systems Unknown device 9037
	Flags: bus master, fast devsel, latency 0
	Memory at fc100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 90a6
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1820 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 90a6
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1840 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 90a6
	Flags: bus master, medium devsel, latency 0, IRQ 17
	Memory at fc404800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Elitegroup Computer Systems Unknown device 90a6
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fc400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f6000000-f7ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Elitegroup Computer Systems Unknown device 90a6
	Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Elitegroup Computer Systems Unknown device 90a6
	Capabilities: [a0] Power Management version 2

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: fa000000-fbffffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000f5ffffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Elitegroup Computer Systems Unknown device 90a6
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 90a6
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1860 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 90a6
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 90a6
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 18a0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 90a6
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at fc404c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Capabilities: [50] Subsystem: Gammagraphx, Inc. Unknown device 0000

00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
	Subsystem: Elitegroup Computer Systems Unknown device 90a6
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Elitegroup Computer Systems Unknown device 90a6
	Flags: bus master, medium devsel, latency 0, IRQ 255
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Elitegroup Computer Systems Unknown device 90a6
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at 1c00 [size=8]
	I/O ports at 18d4 [size=4]
	I/O ports at 18d8 [size=8]
	I/O ports at 18d0 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at fc404000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] #12 [0010]

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Elitegroup Computer Systems Unknown device 90a6
	Flags: medium devsel, IRQ 10
	Memory at 88000000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c20 [size=32]

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1001
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f8000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [e0] Express Legacy Endpoint IRQ 0

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 1108
	Flags: bus master, fast devsel, latency 0, IRQ 18
	I/O ports at 4000 [size=256]
	Memory at fa000000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at f4000000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Vital Product Data
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
	Capabilities: [60] Express Endpoint IRQ 0
	Capabilities: [84] Vendor Specific Information

Any idea? :p

---

### Post by WiNeOS on 2007-05-28
Partialy solved.

I went to intellinuxgraphics.org to compile the lastest intel drivers and I read this from the documentation:

> 3.1 Agpgart

To compile agpgart, you must recompile kernel.

Note: from kernel 2.6.20, agpgart can only build into kernel rather than building as modules.

Feisty comes with a 2.6.20-15 kernel and in the configuration It include agpgart like a module. Therefore, I recompiled the kernel including agpgart inside and now, when boot, I have agpgart device in /dev.

Xorg runs with intel driver but in 16bits of color depth... xorg.conf have 24bits how preferred color depth so It's solved in part. :(

---

