---
title: "ATI RADEON 9550 problems in lucid"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by alabuntu on 2010-08-13
Hi people...
I love Ubuntu so much but when my previous graphic card passed away a technicien installed on my desktop an Ati Radeon 9550, my question is what I have to do to watch smooth videos in streaming?
thanks

---

### Post by mörgæs on 2010-08-13
Since the problem is streaming, are you sure that the graphic card and not the band width is to blame?

---

### Post by alabuntu on 2010-08-27
yes sure...now I am in dual boot windows 7 and ubuntu lucid and the situation is slightly improved but not enough to be satisfied

---

### Post by mörgæs on 2010-08-27
Please post the output of

```
hwinfo --gfxcard
```

---

### Post by Zirts on 2010-08-27
Having this card too, the 128MB one.

Videos play fine if they are not on some super HD+++++ mode, but if you want to play games, then things are really f**ked up.

You get about 10FPS or less in Doom3 Linux native client with everything set to minimum and with a lot of manual tweaks in doom3.conf.

---

### Post by alabuntu on 2010-08-29
> **mörgæs said:**
> Please post the output of

```
hwinfo --gfxcard
```
  hwinfo --gfxcard
22: PCI 100.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4153
  Unique ID: VCu0.djvGTZQg_lF
  Parent ID: vSkL.i8os9252y4E
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "ATI RV350 AS"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4153 "RV350 AS"
  SubVendor: pci 0x174b "PC Partner Limited"
  SubDevice: pci 0x0810 
  Driver: "radeon"
  Driver Modules: "drm"
  Memory Range: 0xe0000000-0xefffffff (rw,prefetchable)
  I/O Ports: 0xd800-0xd8ff (rw)
  Memory Range: 0xbf800000-0xbf80ffff (rw,non-prefetchable)
  Memory Range: 0xdffe0000-0xdfffffff (ro,prefetchable,disabled)
  IRQ: 16 (8852 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d00004153sv0000174Bsd00000810bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: radeon
  Driver Info #1:
    XFree86 v4 Server Module: radeon
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #10 (PCI bridge)

23: PCI 100.1: 0380 Display controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4173
  Unique ID: NXNs.ed7ZMribTR3
  Parent ID: vSkL.i8os9252y4E
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.1
  SysFS BusID: 0000:01:00.1
  Hardware Class: graphics card
  Model: "ATI RV350 AS [Radeon 9550] (Secondary)"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4173 "RV350 AS [Radeon 9550] (Secondary)"
  SubVendor: pci 0x174b "PC Partner Limited"
  SubDevice: pci 0x0811 
  Memory Range: 0xc0000000-0xcfffffff (rw,prefetchable)
  Memory Range: 0xbf000000-0xbf00ffff (rw,non-prefetchable)
  Module Alias: "pci:v00001002d00004173sv0000174Bsd00000811bc03sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #10 (PCI bridge)

Primary display adapter: #22

---

### Post by mörgæs on 2010-08-29
You are using the open source 'radeon' driver, and according to this
[http://ubuntuforums.org/showthread.php?t=1545344](http://ubuntuforums.org/showthread.php?t=1545344)
you should not try to change that. 

More here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

If you can wait a little more than a month, you will have the option of trying Ubuntu 10.10. There is a lot of attention on this problem, so maybe we will see an improvement.

---

### Post by mörgæs on 2010-08-29
By the way: As far as I know (somebody please correct me, if I am wrong here) Ubuntu 8.04 uses the last available closed source drivers from ATI. You could give this one a try.

---

### Post by Mark Phelps on 2010-08-31
> **mörgæs said:**
> By the way: As far as I know (somebody please correct me, if I am wrong here) Ubuntu 8.04 uses the last available closed source drivers from ATI.

+1 That is correct.

Furthermore, Ubuntu versions newer than that use a newer Xserver version that is incompatible with the older, legacy ATI drivers.

So, you can't run the older drivers on the newer Ubuntu versions due to that incompatibility.

---

### Post by realzippy on 2010-08-31
Or ask your "technician" to replace the ATI card with a NVIDIA card....he might not knew that it is a bad idea to run
old ATI cards on newer linux OS...

---

