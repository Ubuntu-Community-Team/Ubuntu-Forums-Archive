---
title: "Possibly a borked upgrade to 9.10?"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by ka1ssr on 2009-12-27
Hi!

I recently upgraded from 9.04 to 9.10.  I lost the network connection sometime during the upgrade and may have lost some files.  I started the upgrade and went to sleep.  When I woke up sometime later, I saw a dialog box asking me to restart the computer and I couldn't make a wireless connection to the network (the "enable wireless" item was missing from the network connection applet).  No error message during reboot.

There was one problem with Gnucash when the system rebooted, but that was fixed by reinstalling it.  The system appears to be stable (I'm on it right now) but I would like to know if there is a log file somewhere that would tell me if there were any files skipped?

Thanks!

Bill

---

### Post by efflandt on 2009-12-27
You neglected to say what kind of wireless (for example what does it show up as in **sudo lspci -v** if built-in or **sudo lsusb -v** if USB?).

Does System > Adminstration > Hardware Drivers show any special drivers for your computer?  For example if you have Broadcom wireless, you may need use Synaptic to install bcmwl-kernel-source from the 9.10 CD and/or activate Broadcom STA hardware driver if you have no other network connection available (then reboot).

---

### Post by ka1ssr on 2009-12-27
Ooops!  I goofed and forgot to tell you that my network came back when I booted into the new system.

But in case you were wondering...

```
sudo lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
	Subsystem: ASUSTeK Computer Inc. Device 8017
	Flags: bus master, medium devsel, latency 0
	Memory at e4000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [a0] AGP version 2.0
	Capabilities: [c0] Power Management version 2
	Kernel driver in use: agpgart-via
	Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: c7000000-c7ffffff
	Prefetchable memory behind bridge: c8000000-e3ffffff
	Capabilities: [80] Power Management version 2
	Kernel modules: shpchp

00:04.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
	Subsystem: ASUSTeK Computer Inc. Device 8017
	Flags: bus master, stepping, medium devsel, latency 0

00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10) (prog-if 8a [Master SecP PriP])
	Flags: bus master, stepping, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at b800 [size=16]
	Capabilities: [c0] Power Management version 2
	Kernel driver in use: pata_via

00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
	Subsystem: First International Computer, Inc. Device 1234
	Flags: bus master, medium devsel, latency 32, IRQ 5
	I/O ports at b400 [size=32]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: uhci_hcd

00:04.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
	Flags: medium devsel
	Kernel modules: i2c-viapro

00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
	Flags: bus master, medium devsel, latency 32, IRQ 5
	I/O ports at b000 [size=256]
	Memory at c6800000 (32-bit, non-prefetchable) [size=512]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: rtl8180
	Kernel modules: rtl8180

00:0b.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 02)
	Subsystem: Ensoniq Device 2003
	Flags: bus master, slow devsel, latency 32, IRQ 11
	I/O ports at a800 [size=64]
	Capabilities: [dc] Power Management version 1
	Kernel driver in use: ENS1371
	Kernel modules: snd-ens1371

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
	Subsystem: ATI Technologies Inc Device 2002
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at d800 [size=256]
	Memory at c7800000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at d7fe0000 [disabled] [size=128K]
	Capabilities: [58] AGP version 2.0
	Capabilities: [50] Power Management version 2
	Kernel modules: radeon, radeonfb

01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)
	Subsystem: ATI Technologies Inc Device 2003
	Flags: bus master, 66MHz, medium devsel, latency 64
	Memory at c8000000 (32-bit, prefetchable) [size=128M]
	Memory at c7000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [50] Power Management version 2

```

What I'm worried about is the fact that the system is running without some of its updated packages.  "apt-get upgrade" says that everything is up to date.

Thanks again!

Bill

---

### Post by raymondh on 2009-12-27
> **ka1ssr said:**
> ODE]

What I'm worried about is the fact that the system is running without some of its updated packages.  "apt-get upgrade" says that everything is up to date.

Thanks again!

Bill

Bill,

If you're up-to-date ... then it must be OK.  Otherwise, update manager would show you an error.

Regards,

---

### Post by ka1ssr on 2009-12-27
Hi, Raymond,

Well...yeah...I suppose you're right.  Still a bit bummed that Gnucash needed to be re-installed.

I'll live.

Thanks,

Bill

---

