---
title: "Ubuntu 10.04 klunky and slow"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by techforay on 2010-08-06
I just installed ubuntu 10.04 on a AMD 64 3200 system.  I loads quickly but responds very klunky when scrolling in firefox or opening menus.  I have a ATI Radeon X1300 XI video card.  I wonder if there is a driver issue.  How would I check that?

---

### Post by mörgæs on 2010-08-10
Try posting the output from 

```
hwinfo --gfx
```

---

### Post by lechien73 on 2010-08-10
You could have a look at post #10 of this thread: [http://uri.tl/z](http://uri.tl/z)

It deals with known Lucid issues and workarounds, the proprietary ATI drivers seem to cause an issue.

---

### Post by techforay on 2010-08-10
ray@ray-desktop:~$ hwinfo --gfx
30: PCI 100.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_71ce
  Unique ID: VCu0.wwFxL3ksSZ9
  Parent ID: vSkL.CP+qXDDqow8
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "ATI RV530LE [Radeon X1600]"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x71ce "RV530LE [Radeon X1600]"
  SubVendor: pci 0x1545 "VISIONTEK"
  SubDevice: pci 0x2850 
  Driver: "radeon"
  Driver Modules: "drm"
  Memory Range: 0xd0000000-0xdfffffff (rw,prefetchable)
  Memory Range: 0xe0030000-0xe003ffff (rw,non-prefetchable)
  I/O Ports: 0xd000-0xdfff (rw)
  Memory Range: 0x30000000-0x3001ffff (ro,prefetchable,disabled)
  IRQ: 24 (no events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d000071CEsv00001545sd00002850bc03sc00i00"
  Driver Info #0:
    Driver Status: radeon is active
    Driver Activation Cmd: "modprobe radeon"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)

31: PCI 100.1: 0380 Display controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_71ee
  Unique ID: NXNs.xqTDFL0oxED
  Parent ID: vSkL.CP+qXDDqow8
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.1
  SysFS BusID: 0000:01:00.1
  Hardware Class: graphics card
  Model: "ATI Display controller"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x71ee 
  SubVendor: pci 0x1545 "VISIONTEK"
  SubDevice: pci 0x2851 
  Memory Range: 0xe0020000-0xe002ffff (rw,non-prefetchable,disabled)
  Module Alias: "pci:v00001002d000071EEsv00001545sd00002851bc03sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)

Primary display adapter: #30
ray@ray-desktop:~$

---

### Post by mörgæs on 2010-08-11
The processor seems to be an X1600, but I don't think that makes a big difference. Have you tried installing a driver from here? 

[http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.2&product=&contentType=GPU+Download+Detail&ostype=Linux+x86_64&keywords=&items=20](http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.2&product=&contentType=GPU+Download+Detail&ostype=Linux+x86_64&keywords=&items=20)

Besides that I don't have any ideas, sorry.

---

### Post by techforay on 2010-08-11
I am really new to Linux but yes I have downloaded the drivers from this site.  I right clicked and made the file exeacutable and ran it.  Another folder showed up for a short period of time and then went away.  I am thinking it installed but dont know how to tell for sure

---

