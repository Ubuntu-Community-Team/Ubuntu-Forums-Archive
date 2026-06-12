---
title: "Dell mouse not recognized"
date: 2009-06-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dtessier on 2009-06-03
Strange, after updating everything tonight, my Dell mouse stopped working. If I plug in an old Microsoft mouse, that one works just fine. The Dell mouse shows up in the output of "lsusb -v" and "dmesg", but not in "cat /proc/bus/input/devices"...

```
daniel@hobbes:~$ lsusb -v

Bus 002 Device 005: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x413c Dell Computer Corp.
  idProduct          0x3010 Optical Wheel Mouse
  bcdDevice            2.30
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
      ** UNRECOGNIZED:  09 21 10 01 00 01 22 34 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
<snip>
Bus 003 Device 007: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x045e Microsoft Corp.
  idProduct          0x0040 Wheel Mouse Optical
  bcdDevice            1.21
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
      ** UNRECOGNIZED:  09 21 00 01 00 01 22 48 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)

```

```
daniel@hobbes:~$ dmesg
<snip>
[  452.444017] usb 2-2: new low speed USB device using ohci_hcd and address 5
[  452.649117] usb 2-2: configuration #1 chosen from 1 choice
[  452.661409] input: HID 413c:3010 as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input15
[  452.661520] generic-usb 0003:413C:3010.0009: input,hidraw3: USB HID v1.10 Mouse [HID 413c:3010] on usb-0000:00:02.0-2/input0
<snip>
[  752.709876] usb 3-2.3: new low speed USB device using ohci_hcd and address 7
[  752.831975] usb 3-2.3: configuration #1 chosen from 1 choice
[  752.848329] input: Microsoft Microsoft Wheel Mouse Optical&#65533; as /devices/pci0000:00/0000:00:02.1/usb3/3-2/3-2.3/3-2.3:1.0/input/input16
[  752.848442] generic-usb 0003:045E:0040.000A: input,hidraw2: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical&#65533;] on usb-0000:00:02.1-2.3/input0
daniel@hobbes:~$ 

```

```
daniel@hobbes:~$ cat /proc/bus/input/devices 
<snip>
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=mouse0 event3 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3
<snip>
I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input9
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=045e Product=0040 Version=0100
N: Name="Microsoft Microsoft Wheel Mouse Optical&#65533;"
P: Phys=usb-0000:00:02.1-2.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.1/usb3/3-2/3-2.3/3-2.3:1.0/input/input16
U: Uniq=
H: Handlers=mouse2 event9 
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

daniel@hobbes:~$ 

```

---

### Post by AdrianTM on 2009-06-14
I also have a Dell mouse that doesn't work (but doesn't seem to appear in lspci

lsusb -v list is as: 
> 
Bus 002 Device 002: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x413c Dell Computer Corp.
  idProduct          0x3010 Optical Wheel Mouse
  bcdDevice            2.20
  iManufacturer           0
  iProduct                0
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0
      ** UNRECOGNIZED:  09 21 00 01 00 01 22 34 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10


I'm interested in a fix...

---

### Post by AdrianTM on 2009-06-15
The latest upgrade fixed this issue.

---

### Post by ranch hand on 2009-06-15
I am just lurking with great interest.  I have a Dell mouse (see sig for box) and have no trouble with it at all.

---

