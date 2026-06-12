---
title: "live cd fails to start X"
date: 2006-09-14
forum: Installation &amp; Upgrades
---

### Post by mathfeel on 2006-09-14
I am trying to run the ubuntu livecd for my amd64 machine, everything went find, but X failed to start. The error is:

```
X -verbose
```

```
...
(WW) ATI:  PCI Mach64 in slot 1:0:0 could not be detected!
(WW) ATI:  PCI Mach64 in slot 1:0:1 could not be detected!
(EE) No devices detected.

Fatal server error:
no screens found
```

Here's the info from lspci:

```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] (prog-if 00 [VGA])
	Subsystem: ABIT Computer Corp.: Unknown device 000f
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d1000000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at 9000 [size=256]
	Expansion ROM at d0000000 [disabled] [size=128K]
	Capabilities: <available only to root>

0000:01:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] Secondary
	Subsystem: ABIT Computer Corp.: Unknown device 000e
	Flags: bus master, fast devsel, latency 0
	Memory at d1010000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <available only to root>
```

and the line in xorg.conf that refers to the busid reads:

```
PCI:1:0:0
```

Help me start X please!! Thanks

---

