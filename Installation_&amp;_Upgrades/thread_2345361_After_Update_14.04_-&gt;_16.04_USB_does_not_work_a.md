---
title: "After Update 14.04 -&gt; 16.04 USB does not work anymore for programmer"
date: 2016-12-03
forum: Installation &amp; Upgrades
---

### Post by etelly on 2016-12-03
Hi,

not sure this is the right sub-forum but I have to start somewhere :-)

I am using a microcontroller programmer called USBProg4 connected via USB and the programming software AVRDude.

After updating my LINUX to 16.04 AVRDude does not see the programmer anymore (other USB devices are working fine).

A lsusb shows the programmer correctly (Atmel Corp. AVR ISP mkII):

```
~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 8087:07dc Intel Corp. 
Bus 002 Device 003: ID 5986:0538 Acer, Inc 
Bus 002 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub
Bus 002 Device 009: ID 03eb:2104 Atmel Corp. AVR ISP mkII
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


but a more verbose one shows a problem:

```
~$ sudo lsusb -D /dev/bus/usb/002/009
[sudo] Passwort für etelly: 
Device: ID 03eb:2104 Atmel Corp. AVR ISP mkII
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x03eb Atmel Corp.
  idProduct          0x2104 AVR ISP mkII
  bcdDevice            2.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10

```
Has anybody an idea how to solve this problem?

Thanks,

etelly

---

