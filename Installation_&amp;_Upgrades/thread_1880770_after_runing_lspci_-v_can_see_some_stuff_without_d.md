---
title: "after runing lspci -v can see some stuff without driver"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by Peter2009 on 2011-11-14
```
U run lspci -v
```

and I get this message for this components

```

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Dell Device 022f
	Flags: bus master, fast devsel, latency 0
	Memory at feb00000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	Memory behind bridge: fe300000-fe3fffff
	Capabilities: <access denied>

02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Dell Device 022f
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at fe3ff600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
	Subsystem: Dell Device 022f
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at fe3ff700 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```


I the other ones there is "Kernel driver in use: xxxx and Kernel modules: xxxxx" does this mean the above components has not got a driver installed?

Thanks for your help!

---

