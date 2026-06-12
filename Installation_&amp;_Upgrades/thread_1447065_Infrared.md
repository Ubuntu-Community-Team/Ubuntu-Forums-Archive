---
title: "Infrared"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by Millamber on 2010-04-04
I am new to linux having just abandoned Windows due to stability issues.
 
I have a Hauppage remote with a usb ir reciever.
 
This worked fine under windows using the drivers for the windows media center remote.
 
I can't however get this to work under Linux.
 
What I am really looking for is a method, perhaps using a command line in the terminal window to be able to test and see if the OS has actually detected the device.
 
I have tried irw, but there is no response.
 
If I know that the device is connected, then I can start looking at issues of identifying the correct drivers for the device.
 
Any help or advice is much appreciated.
 
Thanks
 
Millamber

---

### Post by Millamber on 2010-04-04
I have typed in the following lsusb:

The following output:

Bus 007 Device 005: ID 1784:0001 TopSeed Technology Corp. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 1058:1102 Western Digital Technologies, Inc. 
Bus 002 Device 002: ID 04fc:0c15 Sunplus Technology Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 009: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

If I unplug the usb ir reciever, then the line indicated as TopSeed Technology Corp.  disappears.
So I am assuming that this is the IR device.

This is the remote that I have:

[http://www.i-tech.com.au/products/32142_Hauppauge_MCE_Remote_Control_Kit_.aspx](http://www.i-tech.com.au/products/32142_Hauppauge_MCE_Remote_Control_Kit_.aspx)

I also found this:

[http://www.mythtv.org/wiki/MCE_Remote#Support_Status](http://www.mythtv.org/wiki/MCE_Remote#Support_Status)

and this:

[http://ubuntuforums.org/showthread.php?t=1133689](http://ubuntuforums.org/showthread.php?t=1133689)

I am now just confused.  If anyone has any ideas, it will be much appreciated.

Regards

Millamber

---

### Post by conradin on 2010-04-04
in the synaptic package manager) try installing irda-utilis and see if that gives you any options for controlling your device.

---

### Post by Millamber on 2010-04-04
also the output of  
dmesg | grep usb

[    0.196442] usbcore: registered new interface driver usbfs
[    0.196442] usbcore: registered new interface driver hub
[    0.196442] usbcore: registered new device driver usb
[    0.768078] usb usb1: configuration #1 chosen from 1 choice
[    0.784065] usb usb2: configuration #1 chosen from 1 choice
[    0.784265] usb usb3: configuration #1 chosen from 1 choice
[    0.784401] usb usb4: configuration #1 chosen from 1 choice
[    0.784532] usb usb5: configuration #1 chosen from 1 choice
[    0.784662] usb usb6: configuration #1 chosen from 1 choice
[    0.784794] usb usb7: configuration #1 chosen from 1 choice
[    0.784921] usb usb8: configuration #1 chosen from 1 choice
[    1.132009] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.267824] usb 2-1: configuration #1 chosen from 1 choice
[    1.620007] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    1.815278] usbcore: registered new interface driver usb-storage
[    1.816162] usb-storage: device found at 2
[    1.816164] usb-storage: waiting for device to settle before scanning
[    1.828315] usb 3-1: configuration #1 chosen from 1 choice
[    1.839934] usbcore: registered new interface driver hiddev
[    1.972129] input: HID 04d9:0499 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input4
[    1.972176] generic-usb 0003:04D9:0499.0001: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:0499] on usb-0000:00:1a.0-1/input0
[    1.972185] usbcore: registered new interface driver usbhid
[    1.972186] usbhid: v2.6:USB HID core driver
[    2.080006] usb 7-2: new full speed USB device using uhci_hcd and address 2
[    2.258844] usb 7-2: configuration #1 chosen from 1 choice
[    6.816225] usb-storage: device scan complete
[   10.756427] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   10.756429] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   11.208711] usb 7-2: reset full speed USB device using uhci_hcd and address 2
[   11.364077] lirc_mceusb[2]: Topseed eHome Infrared Transceiver on usb7:2
[   11.364096] usbcore: registered new interface driver lirc_mceusb
[16143.804013] usb 1-2: new high speed USB device using ehci_hcd and address 3
[16143.936958] usb 1-2: configuration #1 chosen from 1 choice
[16143.937921] usb-storage: device found at 3
[16143.937923] usb-storage: waiting for device to settle before scanning
[16148.948586] usb-storage: device scan complete
[77537.120045] usb 3-1: USB disconnect, address 2
[77537.388017] usb 3-1: new low speed USB device using uhci_hcd and address 3
[77537.577290] usb 3-1: configuration #1 chosen from 1 choice
[77537.615575] input: HID 04d9:0499 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input6
[77537.615664] generic-usb 0003:04D9:0499.0002: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:0499] on usb-0000:00:1a.0-1/input0
[77553.692025] usb 2-3: new high speed USB device using ehci_hcd and address 4
[77553.970117] usb 2-3: configuration #1 chosen from 1 choice
[77554.019898] usb-storage: device found at 4
[77554.019900] usb-storage: waiting for device to settle before scanning
[77554.086101] input: Western Digital My Book as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.1/input/input7
[77554.086175] generic-usb 0003:1058:1102.0003: input,hidraw1: USB HID v1.11 Device [Western Digital My Book] on usb-0000:00:1d.7-3/input1
[77559.026010] usb-storage: device scan complete
[77674.268043] usb 3-1: USB disconnect, address 3
[77674.536134] usb 3-1: new low speed USB device using uhci_hcd and address 4
[77674.727142] usb 3-1: configuration #1 chosen from 1 choice
[77674.765052] input: HID 04d9:0499 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input8
[77674.765145] generic-usb 0003:04D9:0499.0004: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:0499] on usb-0000:00:1a.0-1/input0
[77729.120128] usb 2-3: USB disconnect, address 4
[77742.068517] usb 2-3: new high speed USB device using ehci_hcd and address 5
[77742.348109] usb 2-3: configuration #1 chosen from 1 choice
[77742.394779] usb-storage: device found at 5
[77742.394782] usb-storage: waiting for device to settle before scanning
[77742.464148] input: Western Digital My Book as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.1/input/input9
[77742.464220] generic-usb 0003:1058:1102.0005: input,hidraw1: USB HID v1.11 Device [Western Digital My Book] on usb-0000:00:1d.7-3/input1
[77747.401464] usb-storage: device scan complete
[82517.208040] usb 7-2: USB disconnect, address 2
[82517.209321] lirc_mceusb[2]: usb remote disconnected
[82523.997035] usb 7-2: new full speed USB device using uhci_hcd and address 3
[82524.170765] usb 7-2: configuration #1 chosen from 1 choice
[82524.284516] usb 7-2: reset full speed USB device using uhci_hcd and address 3
[82524.440952] lirc_mceusb[3]: Topseed eHome Infrared Transceiver on usb7:3
[99150.144019] usb 1-2: USB disconnect, address 3
[99153.792037] usb 3-1: USB disconnect, address 4
[99154.052010] usb 3-1: new low speed USB device using uhci_hcd and address 5
[99154.240916] usb 3-1: configuration #1 chosen from 1 choice
[99154.279082] input: HID 04d9:0499 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input10
[99154.279160] generic-usb 0003:04D9:0499.0006: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:0499] on usb-0000:00:1a.0-1/input0
[99155.280038] usb 3-1: USB disconnect, address 5
[99155.544010] usb 3-1: new low speed USB device using uhci_hcd and address 6
[99155.732920] usb 3-1: configuration #1 chosen from 1 choice
[99155.771068] input: HID 04d9:0499 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input11
[99155.771143] generic-usb 0003:04D9:0499.0007: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:0499] on usb-0000:00:1a.0-1/input0
[99160.240034] usb 3-1: USB disconnect, address 6
[99160.500009] usb 3-1: new low speed USB device using uhci_hcd and address 7
[99160.688934] usb 3-1: configuration #1 chosen from 1 choice
[99160.727082] input: HID 04d9:0499 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input12
[99160.727157] generic-usb 0003:04D9:0499.0008: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:0499] on usb-0000:00:1a.0-1/input0
[99168.920033] usb 3-1: USB disconnect, address 7
[99169.184011] usb 3-1: new low speed USB device using uhci_hcd and address 8
[99169.372959] usb 3-1: configuration #1 chosen from 1 choice
[99169.411107] input: HID 04d9:0499 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input13
[99169.411182] generic-usb 0003:04D9:0499.0009: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:0499] on usb-0000:00:1a.0-1/input0
[99190.720013] usb 1-2: new high speed USB device using ehci_hcd and address 4
[99190.868719] usb 1-2: configuration #1 chosen from 1 choice
[99190.877374] usb-storage: device found at 4
[99190.877376] usb-storage: waiting for device to settle before scanning
[99195.877432] usb-storage: device scan complete
[99260.816020] usb 1-2: USB disconnect, address 4
[99265.640033] usb 3-1: USB disconnect, address 8
[99277.776011] usb 3-2: new low speed USB device using uhci_hcd and address 9
[99277.964618] usb 3-2: configuration #1 chosen from 1 choice
[99278.002764] input: HID 04d9:0499 as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input14
[99278.002842] generic-usb 0003:04D9:0499.000A: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:0499] on usb-0000:00:1a.0-2/input0
[99449.159707] usb 2-3: USB disconnect, address 5
[99468.552015] usb 2-3: new high speed USB device using ehci_hcd and address 7
[99468.830337] usb 2-3: configuration #1 chosen from 1 choice
[99468.876485] usb-storage: device found at 7
[99468.876486] usb-storage: waiting for device to settle before scanning
[99468.943312] input: Western Digital My Book as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.1/input/input15
[99468.943371] generic-usb 0003:1058:1102.000B: input,hidraw1: USB HID v1.11 Device [Western Digital My Book] on usb-0000:00:1d.7-3/input1
[99473.884926] usb-storage: device scan complete
[147197.840038] usb 7-2: USB disconnect, address 3
[147197.840448] lirc_mceusb[3]: usb remote disconnected
[148572.908015] usb 7-2: new full speed USB device using uhci_hcd and address 4
[148573.138114] usb 7-2: configuration #1 chosen from 1 choice
[148573.308013] usb 7-2: reset full speed USB device using uhci_hcd and address 4
[148573.519863] lirc_mceusb[4]: Topseed eHome Infrared Transceiver on usb7:4
[158451.336038] usb 7-2: USB disconnect, address 4
[158451.337934] lirc_mceusb[4]: usb remote disconnected
[158480.280098] usb 2-3: USB disconnect, address 7
[158482.084013] usb 2-4: new high speed USB device using ehci_hcd and address 9
[158482.338891] usb 2-4: configuration #1 chosen from 1 choice
[158482.388041] usb-storage: device found at 9
[158482.388043] usb-storage: waiting for device to settle before scanning
[158482.455251] input: Western Digital My Book as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.1/input/input16
[158482.455315] generic-usb 0003:1058:1102.000C: input,hidraw1: USB HID v1.11 Device [Western Digital My Book] on usb-0000:00:1d.7-4/input1
[158486.004012] usb 7-1: new full speed USB device using uhci_hcd and address 5
[158486.174137] usb 7-1: configuration #1 chosen from 1 choice
[158486.288014] usb 7-1: reset full speed USB device using uhci_hcd and address 5
[158486.444068] lirc_mceusb[5]: Topseed eHome Infrared Transceiver on usb7:5
[158487.396853] usb-storage: device scan complete

---

### Post by Millamber on 2010-04-04
Hi Conradin,

Thanks, being new to Linux let me ask a stupid question:

By synaptic package manager do you mean the Ubuntu Software System?

I tried searching in their for irda, but nothing is found.

Millamber

---

### Post by Millamber on 2010-04-04
Sorry Conradin,

Found the synaptic package manager and installed the irda utilities.

How do I now access those utilities?

Regards

Millamber

---

### Post by conradin on 2010-04-05
This package contains userspace utilities to manage and handle infrared
devices. It includes irattach, findchip, irdadump, irdaping and irpsion5.

try reading the manual pages for any of the programs listed, or running them as a superuser
```

man irattach
sudo irattach

```

---

