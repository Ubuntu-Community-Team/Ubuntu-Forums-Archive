---
title: "Gutsy Gibbon - Cannot allocate resource region"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by TrueWater on 2007-11-23
Hi,

I've been using Feisty for a pretty long time, but now decided to update to Gutsy. After installing using the default upgrade button in Update Manager, my PC won't boot, and gives me this error:
```
[37.411013] PCI: Cannot allocate resource region 1 of device 0000:00:14.0
```
I reinstalled Feisty and did a 'lspci -v' and searched for device 0000:00:14.0, and found this:
```
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 13)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7326
	Flags: 66MHz, medium devsel
	I/O ports at 0b00 [size=16]
	Memory at 40000000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7326
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f900 [size=16]
	Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7326
	Flags: bus master, slow devsel, latency 64, IRQ 17
	Memory at fdff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7326
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fdb00000-fdbfffff
	Prefetchable memory behind bridge: fda00000-fdafffff
```
I'm not sure what this means, I tried install directly from a new Gutsy Gibbon disk too, but it wouldn't even boot the LiveCD (same error as with upgrade installation), let alone install. Is one of the hardware pieces incompatible with the new kernel? If so, is there a way to get around this without replacing any hardware?

All help is greatly appreciated :) If you need more information, just ask.

Thanks,
TrueWater

---

### Post by TrueWater on 2007-12-21
It has been 4 weeks now, and not a single reply. Anyone?

---

### Post by Beemo on 2008-01-03
I am having similar problems after upgrading to Gusty from Feisty on my AMD64-bit machine.  I'm out of my depth as far as de-bugging goes, but saw some stuff posted by Linus Torvalds himself regarding this issue a couple of weeks ago.

[http://groups.google.com/group/linux.kernel/browse_thread/thread/98291cc5f75efec/2125e2b2560ed195?lnk=st&q=cannot+allocate+resource+region#2125e2b2560ed195](http://groups.google.com/group/linux.kernel/browse_thread/thread/98291cc5f75efec/2125e2b2560ed195?lnk=st&q=cannot+allocate+resource+region#2125e2b2560ed195)

Good Luck,
-Beemo.

---

