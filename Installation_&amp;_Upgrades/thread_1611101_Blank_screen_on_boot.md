---
title: "Blank screen on boot"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by silicoid on 2010-11-01
Hi

I have a HP EliteBook 2730p. lspci reports this for my graphic card:

```

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
        Subsystem: Hewlett-Packard Company Device 30eb
        Flags: bus master, fast devsel, latency 0, IRQ 30
        Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
        Memory at 80000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 6138 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

```

I updated from Lucid to Maverick. When I boot with the new 2.6.35-22 kernel the screen stays blank after grub. When I boot the old 2.6.32-25 Kernel everything works fine. I tried to boot 2.6.35-22 in Recovery Mode. When I do this I see some kernel messages in text mode and then the screen goes blank again.

Same problem with the live system booting from usb.

Any suggestions?

---

### Post by mörgæs on 2010-11-02
There are lots of reports that old kernels are working better than 2.6.35. A good solution is simply to stick to the old, and when a new one appears in the updates, you could give it a try.

---

