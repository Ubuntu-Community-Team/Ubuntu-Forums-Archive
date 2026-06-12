---
title: "Sound card not installed"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by tsqueezer on 2010-05-02
A friend installed Xubuntu just yesterday. I am a user of this system for about 17 hours. He forgot to install the sound card, so I have 0 sound. Looking at the device manager, it appears my sound is: HDA VIA VT82xx. Please tell me how to get my sound card to work. I've got an old computer; previously I was using Windows 2000.

---

### Post by dino99 on 2010-05-02
install with synaptic (system admin synaptic): paprefs and alsamixer

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

maybe better help on xubuntu forum

---

### Post by tsqueezer on 2010-05-02
I'm following the links and instructions, but I'm hopelessly confused. I know at least that the family of sound cards I have are supposed to be supported, not sure about the specific one. How do I get to Xubuntu forum?

---

### Post by tsqueezer on 2010-05-02
Using the terminal, I got this far:

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
        Subsystem: Biostar Microtech Int'l Corp Device 3206
        Flags: bus master, medium devsel, latency 32, IRQ 23
        I/O ports at d400 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20)
        Subsystem: Biostar Microtech Int'l Corp Device 3206
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at fdfff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
        Subsystem: Biostar Microtech Int'l Corp Device 3206
        Flags: medium devsel
        Capabilities: <access denied>
        Kernel modules: i2c-viapro

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
        Subsystem: VIA Technologies, Inc. Device 337e
        Flags: bus master, medium devsel, latency 32
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
        Subsystem: Biostar Microtech Int'l Corp Device 2200
        Flags: bus master, medium devsel, latency 32, IRQ 23
        I/O ports at d000 [size=256]
        Memory at fdffe000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: via-rhine
        Kernel modules: via-rhine

00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
        Flags: fast devsel
        Capabilities: <access denied>

00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge (prog-if 01)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0

---

### Post by tsqueezer on 2010-05-02
I'm working on this in another forum. If I could delete this thread here, I would.

---

