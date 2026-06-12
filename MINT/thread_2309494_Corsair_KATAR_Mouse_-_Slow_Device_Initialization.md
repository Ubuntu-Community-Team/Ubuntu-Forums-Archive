---
title: "Corsair KATAR Mouse - Slow Device Initialization"
date: 2016-01-11
forum: MINT
---

### Post by Kirk Schnable on 2016-01-11
Hello,

I am experiencing a slow device initialization with my Corsair KATAR Gaming Mouse.

I have a USB share switch to quickly swap my keyboard and mouse between my Linux box and my Windows gaming PC, with other mice I have had an instant transition, but with this mouse I noticed a huge delay after the transition completed.   At first, I thought it was a problem with the share switch, but after reviewing the log data I found the issue seems to be the initialization of the device driver.

This is the information from my syslog at the time.  My process was to tail the log, toggle the USB switch away from my computer (disconnect the keyboard and mouse) then toggle it back (connect the keyboard and mouse).

Please see the log excerpt below.  The specific problem seems to be:
**Jan 11 03:02:57 Enterprise kernel: [9198863.624409] hid-generic 0003:1B1C:1B22.024B: timeout initializing reports**

```
Jan 11 03:02:00 Enterprise kernel: [9198806.059974] usb 1-2: USB disconnect, device number 48
Jan 11 03:02:00 Enterprise kernel: [9198806.059981] usb 1-2.2: USB disconnect, device number 49
Jan 11 03:02:00 Enterprise acpid: input device has been disconnected, fd 9
Jan 11 03:02:00 Enterprise acpid: input device has been disconnected, fd 10
Jan 11 03:02:00 Enterprise kernel: [9198806.212083] usb 1-2.3: USB disconnect, device number 50
Jan 11 03:02:00 Enterprise acpid: input device has been disconnected, fd 20
Jan 11 03:02:03 Enterprise kernel: [9198809.852271] usb 3-2: new low-speed USB device number 109 using uhci_hcd
Jan 11 03:02:04 Enterprise kernel: [9198810.457076] usb 3-2: New USB device found, idVendor=1631, idProduct=826a
Jan 11 03:02:04 Enterprise kernel: [9198810.457081] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jan 11 03:02:04 Enterprise kernel: [9198810.457084] usb 3-2: Product:  Share Switch 
Jan 11 03:02:04 Enterprise kernel: [9198810.457086] usb 3-2: Manufacturer:  C.C.H 
Jan 11 03:02:04 Enterprise kernel: [9198810.490676] input:  C.C.H   Share Switch  as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/0003:1631:826A.0244/input/input572
Jan 11 03:02:04 Enterprise kernel: [9198810.490912] hid-generic 0003:1631:826A.0244: input,hidraw0: USB HID v1.00 Keyboard [ C.C.H   Share Switch ] on usb-0000:00:1a.0-2/input0
Jan 11 03:02:04 Enterprise kernel: [9198810.522288] input:  C.C.H   Share Switch  as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/0003:1631:826A.0245/input/input573
Jan 11 03:02:04 Enterprise kernel: [9198810.522599] hid-generic 0003:1631:826A.0245: input,hidraw1: USB HID v1.00 Mouse [ C.C.H   Share Switch ] on usb-0000:00:1a.0-2/input1
Jan 11 03:02:04 Enterprise mtp-probe: checking bus 3, device 109: "/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2"
Jan 11 03:02:04 Enterprise mtp-probe: bus: 3, device: 109 was not an MTP device
Jan 11 03:02:23 Enterprise kernel: [9198829.292228] usb 3-2: USB disconnect, device number 109
Jan 11 03:02:23 Enterprise acpid: input device has been disconnected, fd 9
Jan 11 03:02:23 Enterprise acpid: input device has been disconnected, fd 10
Jan 11 03:02:26 Enterprise kernel: [9198832.936054] usb 1-2: new high-speed USB device number 52 using ehci-pci
Jan 11 03:02:27 Enterprise kernel: [9198833.069369] usb 1-2: New USB device found, idVendor=05e3, idProduct=0608
Jan 11 03:02:27 Enterprise kernel: [9198833.069375] usb 1-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Jan 11 03:02:27 Enterprise kernel: [9198833.069379] usb 1-2: Product: USB2.0 Hub
Jan 11 03:02:27 Enterprise kernel: [9198833.069931] hub 1-2:1.0: USB hub found
Jan 11 03:02:27 Enterprise kernel: [9198833.070239] hub 1-2:1.0: 4 ports detected
Jan 11 03:02:27 Enterprise kernel: [9198833.344387] usb 1-2.2: new low-speed USB device number 53 using ehci-pci
Jan 11 03:02:27 Enterprise kernel: [9198833.440887] usb 1-2.2: New USB device found, idVendor=0b38, idProduct=0010
Jan 11 03:02:27 Enterprise kernel: [9198833.440894] usb 1-2.2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Jan 11 03:02:27 Enterprise kernel: [9198833.445305] input: HID 0b38:0010 as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.2/1-2.2:1.0/0003:0B38:0010.0246/input/input574
Jan 11 03:02:27 Enterprise kernel: [9198833.445613] hid-generic 0003:0B38:0010.0246: input,hidraw0: USB HID v1.10 Keyboard [HID 0b38:0010] on usb-0000:00:1a.7-2.2/input0
Jan 11 03:02:27 Enterprise kernel: [9198833.450399] input: HID 0b38:0010 as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.2/1-2.2:1.1/0003:0B38:0010.0247/input/input575
Jan 11 03:02:27 Enterprise kernel: [9198833.450681] hid-generic 0003:0B38:0010.0247: input,hidraw1: USB HID v1.10 Device [HID 0b38:0010] on usb-0000:00:1a.7-2.2/input1
Jan 11 03:02:27 Enterprise kernel: [9198833.520378] usb 1-2.3: new full-speed USB device number 54 using ehci-pci
Jan 11 03:02:27 Enterprise kernel: [9198833.614748] usb 1-2.3: New USB device found, idVendor=1b1c, idProduct=1b22
Jan 11 03:02:27 Enterprise kernel: [9198833.614753] usb 1-2.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jan 11 03:02:27 Enterprise kernel: [9198833.614755] usb 1-2.3: Product: Corsair Gaming KATAR Mouse
Jan 11 03:02:27 Enterprise kernel: [9198833.614758] usb 1-2.3: Manufacturer: Corsair
Jan 11 03:02:27 Enterprise kernel: [9198833.614760] usb 1-2.3: SerialNumber: 04040017AEAA1003550D7724F5001940
Jan 11 03:02:27 Enterprise kernel: [9198833.616793] input: Corsair Corsair Gaming KATAR Mouse as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.3/1-2.3:1.0/0003:1B1C:1B22.0248/input/input576
Jan 11 03:02:27 Enterprise kernel: [9198833.617054] hid-generic 0003:1B1C:1B22.0248: input,hidraw2: USB HID v1.11 Mouse [Corsair Corsair Gaming KATAR Mouse] on usb-0000:00:1a.7-2.3/input0
Jan 11 03:02:37 Enterprise kernel: [9198843.624387] hid-generic 0003:1B1C:1B22.0249: usb_submit_urb(ctrl) failed: -1
Jan 11 03:02:37 Enterprise kernel: [9198843.624410] hid-generic 0003:1B1C:1B22.0249: timeout initializing reports
Jan 11 03:02:37 Enterprise kernel: [9198843.624557] input: Corsair Corsair Gaming KATAR Mouse as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.3/1-2.3:1.1/0003:1B1C:1B22.0249/input/input577
Jan 11 03:02:37 Enterprise kernel: [9198843.624962] hid-generic 0003:1B1C:1B22.0249: input,hidraw3: USB HID v1.11 Mouse [Corsair Corsair Gaming KATAR Mouse] on usb-0000:00:1a.7-2.3/input1
Jan 11 03:02:47 Enterprise kernel: [9198853.624276] hid-generic 0003:1B1C:1B22.024A: timeout initializing reports
Jan 11 03:02:47 Enterprise kernel: [9198853.624545] hid-generic 0003:1B1C:1B22.024A: hiddev0,hidraw4: USB HID v1.11 Device [Corsair Corsair Gaming KATAR Mouse] on usb-0000:00:1a.7-2.3/input2
Jan 11 03:02:57 Enterprise kernel: [9198863.624409] hid-generic 0003:1B1C:1B22.024B: timeout initializing reports
Jan 11 03:02:57 Enterprise kernel: [9198863.624836] hid-generic 0003:1B1C:1B22.024B: hiddev0,hidraw5: USB HID v1.11 Device [Corsair Corsair Gaming KATAR Mouse] on usb-0000:00:1a.7-2.3/input3
Jan 11 03:02:57 Enterprise mtp-probe: checking bus 1, device 53: "/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.2"
Jan 11 03:02:57 Enterprise mtp-probe: checking bus 1, device 54: "/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.3"
Jan 11 03:02:57 Enterprise mtp-probe: bus: 1, device: 53 was not an MTP device
Jan 11 03:02:57 Enterprise mtp-probe: bus: 1, device: 54 was not an MTP device
```

I am running Linux Mint 17.3 MATE (Ubuntu base) with kernel 3.16.0-38-generic.

 Here is a syslog excerpt where I unplug the mouse only, then plug it back in.

```
Jan 11 03:31:50 Enterprise kernel: [  107.805140] usb 1-2.3: USB disconnect, device number 4
Jan 11 03:31:50 Enterprise acpid: input device has been disconnected, fd 12
Jan 11 03:31:52 Enterprise kernel: [  109.540266] usb 1-2.3: new full-speed USB device number 5 using ehci-pci
Jan 11 03:31:52 Enterprise kernel: [  109.620305] usb 1-2.3: device descriptor read/64, error -32
Jan 11 03:31:52 Enterprise kernel: [  109.818772] usb 1-2.3: New USB device found, idVendor=1b1c, idProduct=1b22
Jan 11 03:31:52 Enterprise kernel: [  109.818778] usb 1-2.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jan 11 03:31:52 Enterprise kernel: [  109.818782] usb 1-2.3: Product: Corsair Gaming KATAR Mouse
Jan 11 03:31:52 Enterprise kernel: [  109.818785] usb 1-2.3: Manufacturer: Corsair
Jan 11 03:31:52 Enterprise kernel: [  109.818788] usb 1-2.3: SerialNumber: 04040017AEAA1003550D7724F5001940
Jan 11 03:31:52 Enterprise kernel: [  109.820563] input: Corsair Corsair Gaming KATAR Mouse as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.3/1-2.3:1.0/0003:1B1C:1B22.0007/input/input17
Jan 11 03:31:52 Enterprise kernel: [  109.820776] hid-generic 0003:1B1C:1B22.0007: input,hidraw2: USB HID v1.11 Mouse [Corsair Corsair Gaming KATAR Mouse] on usb-0000:00:1a.7-2.3/input0
Jan 11 03:32:02 Enterprise kernel: [  119.820287] hid-generic 0003:1B1C:1B22.0008: usb_submit_urb(ctrl) failed: -1
Jan 11 03:32:02 Enterprise kernel: [  119.820315] hid-generic 0003:1B1C:1B22.0008: timeout initializing reports
Jan 11 03:32:02 Enterprise kernel: [  119.820449] input: Corsair Corsair Gaming KATAR Mouse as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.3/1-2.3:1.1/0003:1B1C:1B22.0008/input/input18
Jan 11 03:32:02 Enterprise kernel: [  119.820763] hid-generic 0003:1B1C:1B22.0008: input,hidraw3: USB HID v1.11 Mouse [Corsair Corsair Gaming KATAR Mouse] on usb-0000:00:1a.7-2.3/input1
Jan 11 03:32:12 Enterprise kernel: [  129.820286] hid-generic 0003:1B1C:1B22.0009: timeout initializing reports
Jan 11 03:32:12 Enterprise kernel: [  129.820489] hid-generic 0003:1B1C:1B22.0009: hiddev0,hidraw4: USB HID v1.11 Device [Corsair Corsair Gaming KATAR Mouse] on usb-0000:00:1a.7-2.3/input2
Jan 11 03:32:22 Enterprise mtp-probe: checking bus 1, device 5: "/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.3"
Jan 11 03:32:22 Enterprise kernel: [  139.820288] hid-generic 0003:1B1C:1B22.000A: timeout initializing reports
Jan 11 03:32:22 Enterprise kernel: [  139.820512] hid-generic 0003:1B1C:1B22.000A: hiddev0,hidraw5: USB HID v1.11 Device [Corsair Corsair Gaming KATAR Mouse] on usb-0000:00:1a.7-2.3/input3
Jan 11 03:32:22 Enterprise mtp-probe: bus: 1, device: 5 was not an MTP device
```

Any thoughts would be appreciated!

Thanks,
Kirk


----------
**EDIT: **I found this page, it may hold the key to a solution to this issue: [http://forums.linuxmint.com/viewtopic.php?t=156993&p=812932](http://forums.linuxmint.com/viewtopic.php?t=156993&p=812932)
I will try this tonight when I am around this computer again.

---

### Post by howefield on 2016-01-11
Thread moved to the "*MINT*" forum.

---

