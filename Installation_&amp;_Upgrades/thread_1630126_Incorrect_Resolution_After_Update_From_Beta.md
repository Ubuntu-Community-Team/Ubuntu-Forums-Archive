---
title: "Incorrect Resolution After Update From Beta"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by tdrusk on 2010-11-24
I was running Ubuntu 10.10 Beta and everything worked great. I upgraded one time and now my screen resolution is wrong. I have tried many things, but I would like to start troubleshooting from scratch.

The computer is a Dell Inspiron 537 Desktop. It is using 1024x768 resolution, when it should be using 1280x1024.

Any help is greatly appreciated.

```
$ lspci -v
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
    Subsystem: Dell Device 02e1
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 02e1
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at fe400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at cc00 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: Dell Device 02e1
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fe9f4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 80000000-801fffff
    Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fea00000-feafffff
    Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device 02e1
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at c880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device 02e1
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at c800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device 02e1
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at c480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device 02e1
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at c400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: Dell Device 02e1
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fe9fb400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: Dell Device 02e1
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Device 02e1
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at c080 [size=8]
    I/O ports at c000 [size=4]
    I/O ports at bc00 [size=8]
    I/O ports at b880 [size=4]
    I/O ports at b800 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
    Subsystem: Dell Device 02e1
    Flags: medium devsel, IRQ 5
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Dell Device 02e1
    Flags: bus master, fast devsel, latency 0, IRQ 42
    I/O ports at d800 [size=256]
    Memory at fdfff000 (64-bit, prefetchable) [size=4K]
    Memory at fdfe0000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at feae0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

03:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
    Subsystem: Conexant Systems, Inc. Dimension 3000
    Flags: bus master, medium devsel, latency 64, IRQ 5
    Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
    I/O ports at ec00 [size=8]
    Capabilities: <access denied>

```

---

### Post by itang sanjana on 2010-11-24
Same problem here. Configuring xorg.conf file is the only solution to me. perhaps you should give it a try too .. HTH

---

### Post by tdrusk on 2010-11-24
> **itang sanjana said:**
> Same problem here. Configuring xorg.conf file is the only solution to me. perhaps you should give it a try too .. HTH


I have done that. It works one time,then I reboot and it doesn't work. Other times the xorg.conf Is deleted without my consent. Really weird.

---

### Post by tdrusk on 2010-11-25
Magically it worked this morning after a hard shutdown.

Essentially, KMS was turned off when Ubuntu upgraded from beta. 

I added this to /etc/initramfs-tools
```
# Enable Kernel Modesetting
intel_agp
drm
i915 modeset=1

```

then```

sudo update-initramfs
```
 
I also had to make sure KMS was not blacklisted(from previous guides that I followed to "fix" my resolution"

So in conclusion, if your resolution was good before beta and you know you have an intel graphics card, this may be what you need.

---

### Post by dino99 on 2010-11-25
be aware of custom settings conflicting with the builtin default kernel config: now X is drived by kernel so xorg.conf is not needed and often old ones break X.

---

