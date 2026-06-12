---
title: "USB devices don't mount in Gutsy"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by pinkunicorn on 2007-11-10
I have a Gutsy system installed fresh from CD. When I insert a USB flash disk I get this in /var/log/messages:

```
Nov 10 20:34:41 owl kernel: [  248.064000] usb 1-7.1: new high speed USB device using ehci_hcd and address 5
Nov 10 20:34:41 owl kernel: [  248.168000] usb 1-7.1: configuration #1 chosen from 1 choice
Nov 10 20:34:41 owl kernel: [  248.168000] scsi5 : SCSI emulation for USB Mass Storage devices
Nov 10 20:34:41 owl kernel: [  248.168000] usb 1-7.4: USB disconnect, address 4
Nov 10 20:34:41 owl kernel: [  248.244000] usb 1-7.4: new full speed USB device using ehci_hcd and address 6
Nov 10 20:34:41 owl kernel: [  248.500000] usb 1-7.4: configuration #1 chosen from 1 choice
Nov 10 20:34:41 owl kernel: [  248.500000] scsi6 : SCSI emulation for USB Mass Storage devices
Nov 10 20:34:46 owl kernel: [  253.172000] scsi 5:0:0:0: Direct-Access     U2140703 FLASH DISK       2.00 PQ: 0 ANSI: 2
Nov 10 20:34:46 owl kernel: [  253.624000] scsi 6:0:0:0: Direct-Access     TEAC     FD-05PUB         1026 PQ: 0 ANSI: 0 CCS
Nov 10 20:34:50 owl kernel: [  257.140000] ready
Nov 10 20:34:50 owl kernel: [  257.140000] sd 5:0:0:0: [sda] 2019328 512-byte hardware sectors (1034 MB)
Nov 10 20:34:50 owl kernel: [  257.144000] sd 5:0:0:0: [sda] Write Protect is off
Nov 10 20:34:50 owl kernel: [  257.156000] sd 5:0:0:0: [sda] 2019328 512-byte hardware sectors (1034 MB)
Nov 10 20:34:50 owl kernel: [  257.156000] sd 5:0:0:0: [sda] Write Protect is off
Nov 10 20:34:50 owl kernel: [  257.156000]  sda: sda1
Nov 10 20:34:50 owl kernel: [  257.160000] sd 5:0:0:0: [sda] Attached SCSI removable disk
Nov 10 20:34:50 owl kernel: [  257.160000] sd 5:0:0:0: Attached scsi generic sg0 type 0
Nov 10 20:34:50 owl kernel: [  257.464000] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Nov 10 20:34:50 owl kernel: [  257.464000] sd 6:0:0:0: Attached scsi generic sg1 type 0
Nov 10 20:35:29 owl kernel: [  296.564000] end_request: I/O error, dev fd0, sector 0
Nov 10 20:35:42 owl kernel: [  308.736000] end_request: I/O error, dev fd0, sector 0
```

The flash disk doesn't get mounted, though.

In my previous Feisty installation, flash disks automatically got mounted and appeared as icons on the desktop. How do I get them to mount in the same way in Gutsy.

---

### Post by treacle boy on 2007-11-10
i have had the same problem, my iriver player does not appear as an icon in Places-Computer or on the Desktop like it used to. strangly ifp works with it. Anyway I found this link which I intend to have a play with when I have the time:

[http://www.linuxquestions.org/questions/linux-general-1/make-removable-usb-hdd-mount-at-fixed-mount-point-511917/](http://www.linuxquestions.org/questions/linux-general-1/make-removable-usb-hdd-mount-at-fixed-mount-point-511917/)

Good luck,

Treacle boy

---

