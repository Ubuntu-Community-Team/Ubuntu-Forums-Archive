---
title: "Can't install Intel Graphics Drivers"
date: 2016-03-22
forum: Installation &amp; Upgrades
---

### Post by MrMichaelHill on 2016-03-22
Hello all,

I have installed Xubuntu 14.04 on a  new Toshiba Tecra Z40t-b-106

It has installed some default Intel graphics stuff but when the laptop resumes from sleep all my windows are just black squares and I cannot adjust the brightness using the hotkeys on my laptop so I feel that installing the proper Intel drivers would resolve most of this yeah?

Anyway I've downloaded the installer from Intel (01) and I receive the following error.

```
You don't seem to have an Intel i915 chipset so no updates are needed
```

Here is the output from lspci -vnn

```

 VGA compatible controller [0300]: Intel Corporation Broadwell-U Integrated Graphics [8086:1616] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device [1179:0004]
    Flags: bus master, fast devsel, latency 0, IRQ 64
    Memory at f0000000 (64-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

```

Thanks

---

### Post by grahammechanical on 2016-03-22
Have you installed a proprietary video driver for that Nvidia GTX660 that you list as your hardware? Are you switching back to the integrated Intel graphic adapter before trying to update the Intel video driver? Or, before putting the machine to sleep? Or, does that hardware spec not apply?

Regards.

---

### Post by MrMichaelHill on 2016-03-22
Hi sorry that is a different system! 

This is on a brand new laptop.

Thank you

---

### Post by mastablasta on 2016-03-22
have you tried to install with PPA? or use a latest version of the OS (15.10) or if you are not afraid 16.04 development version?

---

### Post by MrMichaelHill on 2016-03-22
I've tried something of a PPA, can you let me know which one you have in mind?

I'm more of a LTS man!

---

### Post by MrMichaelHill on 2016-03-30
Bumpy bump?

---

