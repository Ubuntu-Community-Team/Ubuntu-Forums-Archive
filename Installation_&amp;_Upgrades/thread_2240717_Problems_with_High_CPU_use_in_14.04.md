---
title: "Problems with High CPU use in 14.04"
date: 2014-08-21
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2014-08-21
I am having the screen seize up. The only solution is to to ALT-CTRL-1 and then a reboot. Htop shows very high cpu use by Recollindex and Compix. This was not a problem in 12.04.

How should I prevent this overuse? It is anoying to find the OS will not respond to normal keyboard pressing and I am having to reboot rather more often than I would prefer, like 2 or  3 times a day.

R

---

### Post by kansasnoob on 2014-08-21
Please post the output of:

```
lspci -v -s `lspci | awk '/VGA/{print $1}'`
```

---

### Post by Robbyx on 2014-08-21
lspci -v -s `lspci | awk '/VGA/{print $1}'`
01:00.0 VGA compatible controller: NVIDIA Corporation G73 [GeForce 7600 GS] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: LeadTek Research Inc. Device 2a52
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f5000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at a000 [size=128]
	[virtual] Expansion ROM at f6000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia

---

### Post by kansasnoob on 2014-08-21
I thought maybe you needed to install the proprietary graphics driver but it seems you already have:

```
 Kernel driver in use: nvidia 
```

---

### Post by Robbyx on 2014-08-21
Do you have any additional suggestions as to how to avoid the excessive cpu useage resulting in the system having to be rebooted?

---

### Post by kansasnoob on 2014-08-23
I had no better answer but probably time for a free bump.

---

### Post by Robbyx on 2014-08-23
I seem to have found the answer in a new release of the kernel. I am using an ssd and I also needed to change such things as the caching in Firefox, but a big thing was to install an edge driver for the video card.

---

