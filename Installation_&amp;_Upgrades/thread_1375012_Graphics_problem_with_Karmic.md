---
title: "Graphics problem with Karmic"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by pft42 on 2010-01-07
Hi,

not sure whether to put this in installation or Hardware or Desktop category. So I'll just start here, ready to be moved :-)

I am trying to install Karmic on a not too brand new PC and got a strange problem with the graphics.

I tried both ubuntu desktop as well as Kubuntu.
The latter is the worst. everything looks fine except any KDE graphics. That means: the taskbar, any menu to be opened from there and the window title line are all scrambled  - nothing to be recognized. its like noise if you know that I mean. Everything else is fine - so far what I have seen. I can right klick on the desktop, select start program and then blindly enter "xterm" and work there.

In ubuntu (gnome version) it looks much better. The only issue I found (after not too much tesxting) is the system monitor. Within this window it is like kde menu just inside the window. Surrounding looks fine here.

The PC is a FSC P4 1,7 Ghz. Graphics card identifies like this:
```

# lspci
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
# hwinfo --gfxcard
19: PCI(AGP) 100.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_5159
  Unique ID: VCu0.G_wQWNYi3c6
  Parent ID: vSkL.mXT7vbpG6dC
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "PC Partner RV100 QY [Sapphire Radeon VE 7000]"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x5159 "Radeon VE"
  SubVendor: pci 0x174b "PC Partner Limited"
  SubDevice: pci 0x7112 "RV100 QY [Sapphire Radeon VE 7000]"
  Memory Range: 0xd8000000-0xdfffffff (rw,prefetchable)
  I/O Ports: 0x3000-0x3fff (rw)
  Memory Range: 0xd0000000-0xd000ffff (rw,non-prefetchable)
  Memory Range: 0xd0020000-0xd003ffff (ro,prefetchable,disabled)
  IRQ: 16 (902 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d00005159sv0000174Bsd00007112bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: radeon
  Driver Info #1:
    XFree86 v4 Server Module: radeon
    3D Support: yes
    Color Depths: 16
    Extensions: dri
    Options: 
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #11 (PCI bridge)

Primary display adapter: #19
```I can't change this card as I do not have another that fits into this PC. 

Any hint where to look is highly appreciated! I'd prefer to get Kubuntu working ;-)

rgds

---

### Post by pft42 on 2010-01-09
Hi,

I just spend some time to install opensuse 11.2, which should use comparable software and kubuntu. 

However this one works fine.

Which config files etc could I compare between the two?

---

### Post by lopita on 2010-01-09
Wow, OpenSUSE actually works?!

---

