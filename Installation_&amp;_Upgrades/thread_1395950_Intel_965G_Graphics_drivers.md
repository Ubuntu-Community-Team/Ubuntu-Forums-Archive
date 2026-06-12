---
title: "Intel 965G Graphics drivers"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by CyberRascal on 2010-02-01
Hi. I installed Xubuntu on an old computer. Running hwinfo --gfxcard yields the following:

[PHP]10: PCI 02.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_2572
  Unique ID: _Znp.mT5AulxdL4B
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel 865 G"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2572 "865 G"
  SubVendor: pci 0x14a4 "GVC/BCM Advanced Research"
  SubDevice: pci 0x2181 
  Revision: 0x02
  Driver: "i915"
  Driver Modules: "drm"
  Memory Range: 0xf0000000-0xf7ffffff (rw,prefetchable)
  Memory Range: 0xfe780000-0xfe7fffff (rw,non-prefetchable)
  I/O Ports: 0xec00-0xec07 (rw)
  IRQ: 16 (17694 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00008086d00002572sv000014A4sd00002181bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: intel
  Driver Info #1:
    XFree86 v4 Server Module: intel
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Primary display adapter: #10
[/PHP]

Anyone know how I would go about installing drivers for this model? Any help is greatly appreciated. :)

---

