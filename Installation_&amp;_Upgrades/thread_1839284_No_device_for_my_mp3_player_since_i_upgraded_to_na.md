---
title: "No device for my mp3 player since i upgraded to natty"
date: 2011-09-05
forum: Installation &amp; Upgrades
---

### Post by swarsron on 2011-09-05
Hello,

i upgraded to natty yesterday. Since then i don't get a device for my mp3 player once i plug it in. I had no problem whatsoever before since it presents itself to the system as a normal usb disk. 
I get this in syslog:
Sep  5 14:55:17 johannes-desktop kernel: [  808.156580] usb 1-2.3: new high speed USB device number 7 using ehci_hcd
Sep  5 14:55:17 johannes-desktop kernel: [  808.266548] scsi11 : usb-storage 1-2.3:1.0

The whole part where it assigns a device is missing. udevadm monitor while i plug it in:
KERNEL[1315227520.439882] add      /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3 (usb)
KERNEL[1315227520.440874] add      /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.0 (usb)
KERNEL[1315227520.441339] add      /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.0/host12 (scsi)
KERNEL[1315227520.441368] add      /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.0/host12/scsi_host/host12 (scsi_host)
UDEV  [1315227520.458585] add      /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3 (usb)
UDEV  [1315227520.461364] add      /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.0 (usb)
UDEV  [1315227520.463403] add      /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.0/host12 (scsi)
UDEV  [1315227520.464844] add      /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.0/host12/scsi_host/host12 (scsi_host)
KERNEL[1315227520.507406] remove   /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.0/host12/scsi_host/host12 (scsi_host)
KERNEL[1315227520.507446] remove   /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.0/host12 (scsi)
UDEV  [1315227520.508019] remove   /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.0/host12/scsi_host/host12 (scsi_host)
UDEV  [1315227520.508205] remove   /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.0/host12 (scsi)

i didn't remove it during that timespan, so i think the problem relates to those "remove" lines. 

lsusb:
Bus 002 Device 004: ID 04b3:300e IBM Corp. 
Bus 002 Device 005: ID 04b3:300f IBM Corp. 
Bus 002 Device 002: ID 04b3:300d IBM Corp. 
Bus 002 Device 003: ID 046d:c50d Logitech, Inc. Cordless Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 0471:2075 Philips (or NXP) 
Bus 001 Device 005: ID 152e:2507 LG (HLDS) 
Bus 001 Device 006: ID 0ccd:0038 TerraTec Electronic GmbH Cinergy TÂ² DVB-T Receiver
Bus 001 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

It's the Philips. The player works on another machine flawlessly so i don't think theres a hardware defect. Plugging in a normal usb-disk works without any problems. I don't have any custom udev rules.

Any ideas? Thank you

---

