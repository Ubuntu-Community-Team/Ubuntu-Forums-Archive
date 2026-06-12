---
title: "my USB driver is not working any more"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by kritik on 2010-09-01
Today one of my USB Sticks stopped to work. It could not be mounted any more. But I see it from lsusb.
```

lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 047: ID 1307:0163 Transcend Information, Inc. 512MB/1GB Flash Drive //However I have 16GB USB stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```and if I see fstab, I don't see my USB
```

sudo fdisk -l
[sudo] password for kritik: 

&#1044;&#1080;&#1089;&#1082; /dev/sda: 120.0 &#1043;&#1041;, 120034123776 &#1073;&#1072;&#1081;&#1090;
255 heads, 63 sectors/track, 14593 cylinders
Units = &#1094;&#1080;&#1083;&#1080;&#1085;&#1076;&#1088;&#1099; of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x96ecc2d4

&#1059;&#1089;&#1090;&#1088;-&#1074;&#1086; &#1047;&#1072;&#1075;&#1088;     &#1053;&#1072;&#1095;&#1072;&#1083;&#1086;       &#1050;&#1086;&#1085;&#1077;&#1094;       &#1041;&#1083;&#1086;&#1082;&#1080;   Id  &#1057;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14593     3004155    5  &#1056;&#1072;&#1089;&#1096;&#1080;&#1088;&#1077;&#1085;&#1085;&#1099;&#1081;
/dev/sda5           14220       14593     3004123+  82  Linux &#1089;&#1074;&#1086;&#1087; / Solaris

```dmesg | tail shows:
```

[30520.612088] usb 1-1: new high speed USB device using ehci_hcd and address 47
[30520.744684] usb 1-1: configuration #1 chosen from 1 choice
[30520.746332] scsi5 : SCSI emulation for USB Mass Storage devices
[30520.746649] usb-storage: device found at 47
[30520.746657] usb-storage: waiting for device to settle before scanning
[30525.744346] usb-storage: device scan complete
[30525.745067] scsi 5:0:0:0: Direct-Access     USBest   USB2FlashStorage 0.00 PQ: 0 ANSI: 2
[30525.758691] sd 5:0:0:0: Attached scsi generic sg2 type 0
[30525.771607] sd 5:0:0:0: [sdb] Attached SCSI removable disk

```What can I do to repair my USB-stick?

---

### Post by lukeiamyourfather on 2010-09-01
I would try to create the partition again plus format it with GParted. If that doesn't do it then it might be toast (they do go bad, more often than people want to think).

---

