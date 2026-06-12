---
title: "Network card: No acpi"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by ubit on 2010-08-27
Hi,

my new home server is based on a msi 785gm-e51 motherboard. I need wake-on-lan. So i configured it in the bios. But the network interface does not show up in /prov/acpi/wakeup.

The part of dmesg:

[FONT="System"][    0.339419] pci 0000:02:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.339433] pci 0000:02:00.0: reg 18 64bit mmio pref: [0xfdfff000-0xfdffffff]
[    0.339442] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xfdff8000-0xfdffbfff]
[    0.339448] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfebe0000-0xfebfffff]
[    0.339474] pci 0000:02:00.0: supports D1 D2
[    0.339476] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.339479] pci 0000:02:00.0: PME# disabled[/FONT]
The system recognizes the network device (pci 02:00.0) and "sees" that PME is supported but than DISABLES PME? Why? And what can i do against this?
System is ubuntu 10.04.1 server x64.

Ciao, Udo

---

