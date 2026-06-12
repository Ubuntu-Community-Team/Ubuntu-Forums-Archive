---
title: "No more network connections after updates"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by lars25700 on 2010-01-09
This morning I was fed updates. 

I'm running VBOX OSE and wanted to access files on my native machine (ubuntu 9.10) from my virtual machine (Windows XP professional) 

Now, I can ping the native host from the XP box, but can't access the share. 

I have tried re-sharing the directory but it won't work. 

Another interesting aspect is that I can't access the VBOX either. It gives me the error: 

"Error: Failed to retrieve share list from server
Please select another viewer and try again." 

Up until this morning it worked just fine. 

Unfortunately I didn't pay attention which software was updated during the process. 

Anyone know what could be wrong here?

---

### Post by derekmbarnes on 2010-01-09
Is your wireless still working in the native system? If not, run "lspci -v | less" and see if the network controller still has its driver; kernel updates seem to have a habit of losing driver installs they don't personally provide.

---

### Post by lars25700 on 2010-01-09
Damn, that was fast - Thanks! 

I don't have wireless on that machine so the only network connection I have is that one. 

Internet access is go. And I can ping in both directions. 

This is what I get when running your command. Any help?


```
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: Fujitsu Technology Solutions Device 1085
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Fujitsu Technology Solutions Device 1085
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18c0 [size=16]
        Memory at c0000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Fujitsu Technology Solutions Device 1085
        Flags: medium devsel, IRQ 11
        I/O ports at 1100 [size=32]
        Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
        Subsystem: ZOTAC International (MCO) Ltd. Device 7046
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at de000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia, nvidiafb

03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
        Subsystem: Fujitsu Technology Solutions Device 1165
        Flags: bus master, fast devsel, latency 0, IRQ 27
        Memory at fc200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: tg3
        Kernel modules: tg3

(END) 

```

---

