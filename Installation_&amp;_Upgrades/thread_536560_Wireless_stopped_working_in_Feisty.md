---
title: "Wireless stopped working in Feisty"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by BrenBarn on 2007-08-27
I have a D-Link DWL-520 wireless card.  It was working perfectly under Dapper.  I upgraded to Edgy with no apparent problems, then upgraded to Feisty.  Now the wireless network isn't working.

lspci gives the following info about my wireless card

00:0e.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
	Subsystem: D-Link System Inc DWL-520 Wireless PCI Adapter, Rev E1
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at ef000000 (32-bit, prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2

What do I need to do to get it working?

An additional note: I am doing everything from single-user console mode because there is some problem with the graphics drivers that is preventing me from loading X.  I believe I need to apt-get new drivers, but I cannot use apt-get until I get a working internet connection.  So I need to know how to do this on the console.

---

