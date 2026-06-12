---
title: "upgraded from 11.04 to 11.10, additional drivers won't work"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by jkossis on 2011-10-20
I recently upgraded to 11.10, and when i click on additional drivers, with my ethernet plugged in, i get "Downloading package indexes failed, please check your network status. Most drivers will not be available." I'm not able to use my wireless because of this. Any help would be greatly appreciated.

My LSPCI is:

lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:308f]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device [103c:308f]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fe980000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at dc80 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at fe940000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:308f]
    Flags: bus master, fast devsel, latency 0
    Memory at fe880000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:308f]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at fe938000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: fea00000-feafffff
    Prefetchable memory behind bridge: 000000003fa00000-000000003fbfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: 000000003f800000-000000003f9fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device [103c:308f]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at dc00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device [103c:308f]
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device [103c:308f]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at d800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device [103c:308f]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device [103c:308f]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fe937c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:308f]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company Device [103c:308f]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
    I/O ports at d400 [size=8]
    I/O ports at d080 [size=4]
    I/O ports at d000 [size=8]
    I/O ports at cc80 [size=4]
    I/O ports at cc00 [size=16]
    Memory at fe937800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1507]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

02:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Hewlett-Packard Company Device [103c:308f]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at febc0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at ec80 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

---

### Post by collisionystm on 2011-10-20
Can you get on the internet?

Open a terminal and type 

ping 8.8.8.8

do you get replies?

---

### Post by jkossis on 2011-10-20
Yes, I am getting continuous ping responses...

---

### Post by collisionystm on 2011-10-20
now ping google.com

responses?

---

### Post by jkossis on 2011-10-20
It says command not found.

---

### Post by collisionystm on 2011-10-20
What did you type?

You typed

ping google.com

right?

---

### Post by jkossis on 2011-10-20
yes. In both the terminal and web browser, neither worked. I am able to access the internet fine, that is not a problem. It is the additional drivers utility that isn't working.

---

