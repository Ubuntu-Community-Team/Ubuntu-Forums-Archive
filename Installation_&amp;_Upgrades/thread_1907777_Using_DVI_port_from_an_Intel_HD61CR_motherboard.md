---
title: "Using DVI port from an Intel HD61CR motherboard"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by dcleal on 2012-01-12
Hi,

I just installed 64-bit 11.10 on a desktop manufactured by Novatech, which is based on an Intel HD61CR motherboard. This all works fine with the monitor connected via VGA, but the monitor stays black and claims not to be receiving a signal if connected via DVI.

I'd like to get the DVI working if I can, but I'm an Ubuntu newbie and struggling to work out where to look. Here's the apparently relevant part of the output from "lspci -v":


```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Intel Corporation Device 200d
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at fe000000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915
```

Which makes it look to my untutored eyes as though the OS hasn't recognised the DVI port. Any suggestions as to where I look next?

Thanks in advance 

- Dave

PS. I do have this vague idea that one day I might run two monitors, one on VGA, the other on DVI, but for now I'd settle for using the DVI port...

---

