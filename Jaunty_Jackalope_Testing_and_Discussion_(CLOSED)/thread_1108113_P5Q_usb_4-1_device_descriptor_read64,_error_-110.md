---
title: "P5Q: usb 4-1: device descriptor read/64, error -110"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by grigio on 2009-03-27
I have the log full of error -110 and -71, is there a bug opened about this?

[    3.808738] ohci1394 0000:04:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.860419] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[febfe000-febfe7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    3.916513] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    4.328009] usb 1-3: device descriptor read/64, error -71
[    4.800010] usb 1-3: device descriptor read/64, error -71
[    5.016064] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    5.140105] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001549b1e]
[    5.340015] usb 1-3: device descriptor read/64, error -71
[    5.385021] kjournald starting.  Commit interval 5 seconds
[    5.385029] EXT3-fs: mounted filesystem with ordered data mode.
[    5.781502] ISO 9660 Extensions: Microsoft Joliet Level 3
[    5.814315] ISO 9660 Extensions: RRIP_1991A
[    6.130689] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[    6.288011] usb 1-3: device descriptor read/64, error -71
[    6.346066] aufs 20080922
[    6.504011] usb 1-3: new high speed USB device using ehci_hcd and address 4
[    7.060006] usb 1-3: device not accepting address 4, error -71
[    7.172011] usb 1-3: new high speed USB device using ehci_hcd and address 5
[    7.600008] usb 1-3: device not accepting address 5, error -71
[    7.600017] hub 1-0:1.0: unable to enumerate USB device on port 3
[    7.976009] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   23.088011] usb 4-1: device descriptor read/64, error -110
[   38.304511] usb 4-1: device descriptor read/64, error -110

---

### Post by danwood76 on 2009-03-27
I get this with my bluetooth dongle.
And my boot actually hung last boot waiting for it.

Do you have a USB bluetooth dongle?

---

### Post by grigio on 2009-03-27
Yes I have a BT usb adapter but I get that msg even when it is not plugged

---

### Post by cjshelley on 2009-04-08
I have a wireless mouse that plugs in via USB and I just installed 8.10 64 bit on my new computer. My mouse works just fine, but during boot I get "[ 2533.436027] USB 5-2: device descriptor read/64 error -110" the message repeats with different numbers in the brackets a few times and then tries "...USB 8-2...read/8 error -110." It then winds up with a message about being unable to enumerate my USB device on port 2. it takes about 5 minutes to boot into intrepid...

---

### Post by grigio on 2009-04-20
I still have this bug at random start up. The poor workaround is to completely switch of the PC and restart again

---

