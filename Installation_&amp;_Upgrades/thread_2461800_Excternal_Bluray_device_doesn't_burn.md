---
title: "Excternal Bluray device doesn't burn"
date: 2021-05-07
forum: Installation &amp; Upgrades
---

### Post by hshl on 2021-05-07
Hi folks,
i purchased a new external blueray device from [HTML=https://www.techpulse120.de/laufwerke/techpulse120-externer-ultrahd-4k-3d-uhd-m-disc-bdxl-usb-3-0-blu-ray-brenner-burner-superdrive-blueray-rom-laufwerk-bd-dvd-cd-ultra-slim-fuer-computer-notebook-ultrabook-windows-mac-os-apple-imac-macbook-pro-air_263_1055]Techpulse120[/HTML] in oder to burn 100 GB MDisc. With Windows10 it works without any trouble, but it doesn't with Ubuntu (20.04). Technically it should since it is also desined for Linux.
A burned Bluray Disc can be read - but if I insert a MDisc blank the error appears: "Blank BD-R can't be mounted - location is already mounted" 
'lsusb' emits:
```

Bus 002 Device 002: ID 13fd:3940 Initio Corporation external DVD burner ECD819-SU3
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 413c:2113 Dell Computer Corp. Dell KB216 Wired Keyboard
Bus 001 Device 002: ID 413c:301a Dell Computer Corp. Dell MS116 USB Optical Mouse
Bus 001 Device 006: ID 0cf3:e005 Qualcomm Atheros Communications 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

'lsusb -v' for BUS 2 emits:
```

Bus 002 Device 002: ID 13fd:3940 Initio Corporation external DVD burner ECD819-SU3
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            0 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         9
  idVendor           0x13fd Initio Corporation
  idProduct          0x3940 external DVD burner ECD819-SU3
  bcdDevice            3.10
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x002c
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              144mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      2 SFF-8020i, MMC-2 (ATAPI)
      bInterfaceProtocol     80 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst               7
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0a  EP 10 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst               7

```

So I wonder if the device is detected correctly ?! If not how can I fix it ? 

Thanks in advance

---

### Post by ajgreeny on 2021-05-07
I've never used blu-ray so have no experience of this but nevertheless this link may help you solve the difficulty you are seeing.
[https://help.ubuntu.com/community/CdDvd/Burning#Blu-Ray_Burning](https://help.ubuntu.com/community/CdDvd/Burning#Blu-Ray_Burning)

---

