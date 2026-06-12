---
title: "auto mount in Ibex not working"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by phillipss@comcast.net on 2008-11-01
I upgraded to Ubuntu 8.10 from 8.04 and my usb hard drive doesn't mount. I went back to 8.04 and it mounts automatically. Can someone help me get the hard drive mounted. The system sses the hard drive?
Thank you

---

### Post by phillipss@comcast.net on 2008-11-01
The iomega drive is shown in the list?


steve@steve-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 059b:0177 Iomega Corp. Hi-Speed USB-to-IDE Bridge Controller
Bus 001 Device 006: ID 03f0:c202 Hewlett-Packard Photosmart 8200 Series
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Any help is very much appreciated.
Thanks,

---

### Post by mixmastamyk on 2008-11-14
Me too.  Automount not working after upgrade to ibex. :(

$ dmesg
[578893.264037] usb 5-8: new high speed USB device using ehci_hcd and address 6
[578893.399510] usb 5-8: configuration #1 chosen from 1 choice
[578893.400643] scsi6 : SCSI emulation for USB Mass Storage devices
[578893.402504] usb-storage: device found at 6
[578893.402519] usb-storage: waiting for device to settle before scanning
[578898.400222] usb-storage: device scan complete
[578898.402439] scsi 6:0:0:0: Direct-Access              USBFlashDrive    PMAP PQ: 0 ANSI: 0 CCS
[578898.619394] sd 6:0:0:0: [sdb] 4030464 512-byte hardware sectors (2064 MB)
[578898.619897] sd 6:0:0:0: [sdb] Write Protect is off
[578898.619905] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[578898.619912] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[578898.622026] sd 6:0:0:0: [sdb] 4030464 512-byte hardware sectors (2064 MB)
[578898.622518] sd 6:0:0:0: [sdb] Write Protect is off
[578898.622527] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[578898.622532] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[578898.622542]  sdb: sdb1
[578898.623487] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[578898.623701] sd 6:0:0:0: Attached scsi generic sg2 type 0

lsusb:
Bus 005 Device 006: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive

---

