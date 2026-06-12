---
title: "cannot find internet"
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by jgw on 2011-04-06
I just did a new install on a pc chips p23g motherboard based machine.  This motherboard has a built in 10/100 connector.  When installing I noticed that the connection flashed orange for a bit and then returned to simply flashing slow.  Its my understanding that if you have a green steady light and a flashing orange then there IS a connect.  If this is true then, for some reason the install didn't find it or didn't install a driver for it.  I installed 2 times just to make sure.

Oh, when installing, off the dvd (10.4) it said there was a problem but it would give me a desktop so that I could figure it out.  I am clueless.  There was a box to install and that is what I have been using.  Obviously, I am missing something here.

Thoughts? (thanks)

---

### Post by mikewhatever on 2011-04-06
The output of **lspci** might help figuring out the NIC model, and thus give some useful info to work with. Can you post that here.

---

### Post by jgw on 2011-04-06
thanks for the reply.  I am away from that machine now but I WILL get the data and post it tomorrow.

thanks again!

---

### Post by mikewhatever on 2011-04-07
OK, see you tomorrow.

---

### Post by jgw on 2011-04-07
here is the output for lspci -v  (motherboard specs follow)

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Subsystem: Elitegroup Computer Systems Device 1623
	Flags: bus master, 66MHz, medium devsel, latency 8
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-via
	Kernel modules: via-agp

00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Subsystem: Elitegroup Computer Systems Device 1623
	Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Subsystem: Elitegroup Computer Systems Device 1623
	Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
	Flags: bus master, medium devsel, latency 0
	Kernel modules: via-agp

00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Subsystem: Elitegroup Computer Systems Device 1623
	Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Subsystem: Elitegroup Computer Systems Device 1623
	Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: fca00000-feafffff
	Prefetchable memory behind bridge: eff00000-f7efffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Elitegroup Computer Systems Device 1623
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at ec00 [size=8]
	I/O ports at e880 [size=4]
	I/O ports at e800 [size=8]
	I/O ports at e480 [size=4]
	I/O ports at e400 [size=16]
	I/O ports at e000 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sata_via
	Kernel modules: sata_via

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: Elitegroup Computer Systems Device 1623
	Flags: bus master, medium devsel, latency 32, IRQ 20
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at fc00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_via
	Kernel modules: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: Elitegroup Computer Systems Device 1623
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at dc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: Elitegroup Computer Systems Device 1623
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at d880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: Elitegroup Computer Systems Device 1623
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at d800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: Elitegroup Computer Systems Device 1623
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at d480 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20)
	Subsystem: Elitegroup Computer Systems Device 1623
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at febffc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
	Subsystem: Elitegroup Computer Systems Device 1623
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: i2c-viapro

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Subsystem: Elitegroup Computer Systems Device aa51
	Flags: medium devsel, IRQ 22
	I/O ports at d000 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: VIA 82xx Audio
	Kernel modules: snd-via82xx

01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)
	Subsystem: Elitegroup Computer Systems Device 1623
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f0000000 (32-bit, prefetchable) [size=64M]
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Expansion ROM at feaf0000 [disabled] [size=64K]
	Capabilities: <access denied>

PCChips P23G v3.0
	  Processor Interface:  	Socket 775
	  Form Factor:  	MicroATX
	  Processors Supported:  	Intel Pentium 4
	  	Intel Celeron D
	  	Intel Pentium D
	  	Intel Core 2 Duo
	  Additional Technologies:  	HyperThreading Technology
	  Front Side Bus:  	533MHz
	  	800MHz
	  	1066MHz	
	  Northbridge:  	VIA P4M800 Pro
	  Southbridge:  	VIA VT8237R Plus
	  Memory Supported:  	DDR333 (PC2700)
	  	DDR400 (PC3200)
	  	533MHz DDR2
	  Number of Slots:  	2 184-Pin
	  	2 240-Pin
	  Maximum Memory Supported:  	2GB
	  Channels:  	6 Channels
	  Audio Chipset:  	Realtek ALC655
	  Video Chipset:  	S3 Graphics Unichrome Pro
	  LAN Type:  	10/100 Mbps
	  PS/2 Keyboard Connectors:  	1
	  PS/2 Mouse Connectors:  	1
	  Serial Communication Ports:  	1
	  Parallel Ports:  	1
	  USB Ports (Total):  	8
	  Audio Out Jacks:  	1
	  IDE Headers:  	2
	  FDD Headers:  	1
	  Serial ATA Headers:  
	  ATX Power Connectors:  	1 20-Pin Connector
	  PC Power Connectors:  	1
	  Fan Connectors:  	2
	  VGA Ports:  	1
	  AGP Slots:  	1
	  PCI Slots:  	3
	  Speed:  	8X
	  Length:  	9.600 in. (24.5 cm)
	  Width:  	9.600 in. (24.5 cm)

---

### Post by mikewhatever on 2011-04-08
There is way to much info in the verbose output you posted, but it looks like the networking hardware isn't there. I've even searched for 'ethernet', thinking I may have missed it. If you have Windows on that computer, look up the NIC model in the Device Manager.

---

### Post by jgw on 2011-04-08
It is a "VIA Compatible fast ethernet adaptor".  Since we are dealing with a via chipset I would say it IS a via adaptor.  Windows had no problem at all finding it.  Since I have installed windows I think I will just let it be.  This is a machine I am working over for a friend of mine and thought it might be a good idea to give him a linux machine but, I think, he doesn't care so this will work for him.  The problem remains pesky but I have no clue (other than the setup problem mentioned below.  If my friend doesn't need his machine back fast I can try and install the latest and greatest that I have downloaded and put on a cd and see what happens.

If you don't reply to this, in a couple of days I will mark it solved.


Thanks for the reply.  I will put xp on the system and see what I can find <sigh>  Perhaps the problem resides in the fact that I get the install error that forces me to install from the desktop.  As far as I can tell this is a known problem.  Perhaps I should download the latest and greatest installation program as things may have changed?

---

