---
title: "USB-HD boot stop by 2 sata hdd"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by oryaaaaa on 2006-11-08
Hi

I am always using WindowsXP of NVIDIA RAID. 
I want to connect USB-HDD to want to develop the OpenGL software
of Linux and to use native's Ubuntu 6.10. 

It succeeded in the installation. However, there is one problem. 
**In the start-up, boot stops. **
It skip by reconnecting the USB cable now. 

The same problem occurs even if UUID is specified by setting Grub. 
It is Disable as for the BIOS setting of SATA. 
and,It is Disable as for SATA local driver of the kernel. 

> 
 usbcore: registered new driver usbfs
 usbcore: registered new driver hub
 ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
 ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 201
 PCI: Setting latency timer of device 0000:00:0b.1 to 64
 ehci_hcd 0000:00:0b.1: EHCI Host Controller
 ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
 ehci_hcd 0000:00:0b.1: debug port 1
 PCI: cache line size of 64 is not supported by device 0000:00:0b.1
 ehci_hcd 0000:00:0b.1: irq 201, io mem 0xfe02e000
 ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
 usb usb1: configuration #1 chosen from 1 choice
 hub 1-0:1.0: USB hub found
 hub 1-0:1.0: 8 ports detected
 forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.56.
 ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
 ieee1394: Initialized config rom entry `ip1394'
 ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
 ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 22 (level, low) -> IRQ 209
 PCI: Setting latency timer of device 0000:00:0b.0 to 64
 ohci_hcd 0000:00:0b.0: OHCI Host Controller
 ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
 ohci_hcd 0000:00:0b.0: irq 209, io mem 0xfe02f000
 usb usb2: configuration #1 chosen from 1 choice
 hub 2-0:1.0: USB hub found
 hub 2-0:1.0: 8 ports detected
 ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
 ACPI: PCI Interrupt 0000:03:06.0[A] -> Link [APC4] -> GSI 19 (level, low)
-> IRQ 217
 ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[217]  MMIO=[fdbff000-fdbff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
 usb 1-1: new high speed USB device using ehci_hcd and address 2
 ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
 ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 225
 PCI: Setting latency timer of device 0000:00:14.0 to 64
 forcedeth: using HIGHDMA
 usb 1-1: configuration #1 chosen from 1 choice
 hub 1-1:1.0: USB hub found
 hub 1-1:1.0: 4 ports detected
 usb 1-4: new high speed USB device using ehci_hcd and address 3
 eth0: forcedeth.c: subsystem: 0105b:0caf bound to 0000:00:14.0
 usb 1-4: configuration #1 chosen from 1 choice
 usb 1-5: new high speed USB device using ehci_hcd and address 4
 usb 1-5: configuration #1 chosen from 1 choice
 ohci_hcd 0000:00:0b.0: wakeup
 ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c200011edb1]
 usb 1-1.3: new full speed USB device using ehci_hcd and address 7
 usb 1-1.3: configuration #1 chosen from 1 choice
 usb 1-1.4: new low speed USB device using ehci_hcd and address 8
 usb 1-1.4: configuration #1 chosen from 1 choice
 usbcore: registered new driver libusual
 SCSI subsystem initialized
 Initializing USB Mass Storage driver...
 usb 2-7: new full speed USB device using ohci_hcd and address 2
 usb 2-7: configuration #1 chosen from 1 choice
 usb 2-8: new full speed USB device using ohci_hcd and address 3
 usb 2-8: configuration #1 chosen from 1 choice
 scsi0 : SCSI emulation for USB Mass Storage devices
 usb-storage: device found at 3
 usb-storage: waiting for device to settle before scanning
 scsi1 : SCSI emulation for USB Mass Storage devices
 usb-storage: device found at 4
 usb-storage: waiting for device to settle before scanning
 usbcore: registered new driver usb-storage
 USB Mass Storage support registered.
 usbcore: registered new driver hiddev
 input: Topre Corporation Realforce 106 as /class/input/input0
 input: USB HID v1.11 Keyboard [Topre Corporation Realforce 106] on usb-0000:00:0b.1-1.3
 input: Microsoft Microsoft Trackball Explorer
 as /class/input/input1
 input: USB HID v1.00 Mouse [Microsoft Microsoft Trackball Explorer
 on usb-0000:00:0b.1-1.4
 usbcore: registered new driver usbhid
 drivers/usb/input/hid-core.c: v2.6:USB HID core driver
   Vendor: HTS54104  Model: 0G9AT00           Rev: MB2O
   Type:   Direct-Access                      ANSI SCSI revision: 00
 usb-storage: device scan complete
   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9228
   Type:   Direct-Access                      ANSI SCSI revision: 00
   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9228
   Type:   Direct-Access                      ANSI SCSI revision: 00
 usb-storage: device scan complete
 SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
 sda: Write Protect is off
 sda: Mode Sense: 00 14 00 00
 sda: assuming drive cache: write through
 SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
 sda: Write Protect is off
 sda: Mode Sense: 00 14 00 00
 sda: assuming drive cache: write through

--------------------------------
STOP, USB-HDD's LED Flashing. non-stop flash,but not Access flash 
I do reconnect USB cable, result is following.
--------------------------------

&#12288; sda:<6>usb 1-4: USB disconnect, address 3
 sd 0:0:0:0: SCSI error: return code = 0x00010000
 end_request: I/O error, dev sda, sector 0
 Buffer I/O error on device sda, logical block 0
 sd 0:0:0:0: rejecting I/O to device being removed
 Buffer I/O error on device sda, logical block 0
  unable to read partition table
 sd 0:0:0:0: Attached scsi disk sda
 sd 1:0:0:0: Attached scsi removable disk sda
 sd 1:0:0:1: Attached scsi removable disk sdb
 usb 1-4: new high speed USB device using ehci_hcd and address 9
 usb 1-4: configuration #1 chosen from 1 choice
 scsi2 : SCSI emulation for USB Mass Storage devices
 usb-storage: device found at 9
 usb-storage: waiting for device to settle before scanning
   Vendor: HTS54104  Model: 0G9AT00           Rev: MB2O
   Type:   Direct-Access                      ANSI SCSI revision: 00
 SCSI device sdc: 78140160 512-byte hdwr sectors (40008 MB)
 sdc: Write Protect is off
 sdc: Mode Sense: 00 14 00 00
 sdc: assuming drive cache: write through
 SCSI device sdc: 78140160 512-byte hdwr sectors (40008 MB)
 sdc: Write Protect is off
 sdc: Mode Sense: 00 14 00 00
 sdc: assuming drive cache: write through
  sdc: sdc1 sdc2 sdc3 sdc4
 sd 2:0:0:0: Attached scsi disk sdc
 usb-storage: device scan complete

There is no problem this ahead. 


My japanese trouble report

Ubuntu Japan Forum / USB HDD Boot stops
[http://forum.ubuntulinux.jp/viewtopic.php?id=13](http://forum.ubuntulinux.jp/viewtopic.php?id=13)

Ubuntu Japan Forum / 6.10 USB HDD Install Guide
[http://forum.ubuntulinux.jp/viewtopic.php?id=10](http://forum.ubuntulinux.jp/viewtopic.php?id=10)

Thank you

---

