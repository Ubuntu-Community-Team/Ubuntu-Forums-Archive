---
title: "usb thumb drive won't mount"
date: 2008-07-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mattduckman on 2008-07-29
i confirmed that this is an issue introduced in intrepid, because i tried it on a hardy live cd, and it worked. i have a transcend jf v30 usb thumb drive that won't mount because of some errors about the expected size of the device. here they are:

```

[  219.537307] usb 5-7: new high speed USB device using ehci_hcd and address 3
[  219.672292] usb 5-7: configuration #1 chosen from 1 choice
[  219.786386] usbcore: registered new interface driver libusual
[  219.803275] Initializing USB Mass Storage driver...
[  219.803275] scsi2 : SCSI emulation for USB Mass Storage devices
[  219.803275] usbcore: registered new interface driver usb-storage
[  219.803275] USB Mass Storage support registered.
[  219.803275] usb-storage: device found at 3
[  219.803275] usb-storage: waiting for device to settle before scanning
[  224.812421] usb-storage: device scan complete
[  224.814971] scsi scan: INQUIRY result too short (5), using 36
[  224.814985] scsi 2:0:0:0: Direct-Access                                    PQ: 0 ANSI: 0
[  224.820625] sd 2:0:0:0: [sdb] Sector size 0 reported, assuming 512.
[  224.820625] sd 2:0:0:0: [sdb] 1 512-byte hardware sectors (0 MB)
[  224.820625] sd 2:0:0:0: [sdb] Write Protect is off
[  224.820625] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  224.820625] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  224.823324] sd 2:0:0:0: [sdb] Sector size 0 reported, assuming 512.
[  224.823324] sd 2:0:0:0: [sdb] 1 512-byte hardware sectors (0 MB)
[  224.823324] sd 2:0:0:0: [sdb] Write Protect is off
[  224.823324] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  224.823324] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  224.823324]  sdb: sdb1
[  224.851324]  sdb: p1 exceeds device capacity
[  224.851573] sd 2:0:0:0: [sdb] Attached SCSI disk
[  224.851671] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  225.022363] attempt to access beyond end of device
[  225.022363] sdb: rw=0, want=8200, limit=1
[  225.022363] Buffer I/O error on device sdb1, logical block 0
[  225.023078] attempt to access beyond end of device
[  225.023088] sdb: rw=0, want=8208, limit=1
[  225.023095] Buffer I/O error on device sdb1, logical block 1
[  225.024859] attempt to access beyond end of device
[  225.024869] sdb: rw=0, want=8216, limit=1
[  225.024875] Buffer I/O error on device sdb1, logical block 2
[  225.025731] attempt to access beyond end of device
[  225.025742] sdb: rw=0, want=8224, limit=1
[  225.025748] Buffer I/O error on device sdb1, logical block 3
[  225.026592] attempt to access beyond end of device
[  225.026603] sdb: rw=0, want=8200, limit=1
[  225.026608] Buffer I/O error on device sdb1, logical block 0
[  225.038249] attempt to access beyond end of device
[  225.038249] sdb: rw=0, want=8200, limit=1
[  225.038249] Buffer I/O error on device sdb1, logical block 0
[  225.038249] attempt to access beyond end of device
[  225.038249] sdb: rw=0, want=8208, limit=1
[  225.038249] Buffer I/O error on device sdb1, logical block 1
[  225.038249] attempt to access beyond end of device
[  225.038249] sdb: rw=0, want=8216, limit=1
[  225.038249] Buffer I/O error on device sdb1, logical block 2
[  225.038249] attempt to access beyond end of device
[  225.038249] sdb: rw=0, want=8224, limit=1
[  225.038249] Buffer I/O error on device sdb1, logical block 3
[  225.038249] attempt to access beyond end of device
[  225.038249] sdb: rw=0, want=8200, limit=1
[  225.038249] Buffer I/O error on device sdb1, logical block 0

```

does anyone have any idea what is causing this?

thanks,
matt

---

### Post by lamps06 on 2008-08-21
This is disheartening.  This has been an issue in Hardy since May.  After installing some update (I never did discover which one) I lost support for my USB flash drive and a USB hard drive.  I have seen numerous posts regarding this issue in Hardy.  There have been several workarounds but not all of these have resovled everyone's issues, including my own.  I was seriously hoping that the Ubuntu programmers would take not of this and resolve the issue in 8.10.  But it looks like this may not be the case...

If anyone with any kind of influence on what happens in 8.10 is reading this PLEASE RESOLVE THIS ISSUE!

---

### Post by mattduckman on 2008-08-22
sorry lamps06, but you and i are having different issues. if i understand correctly, you're having a problem with automount, but you can still read and access the data. my problem is worse, where the usb drive can't be mounted at all with mount, and can't be read at all with fdisk. good luck to you on your issue though.

---

### Post by Fitzcarraldo on 2008-09-30
*mattduckman*, it looks like you're having the same problem with your pen drive that I had. Here's how I solved it:

[http://wiki.sabayonlinux.org/index.php?title=HOWTO:_USB_pen_drive_will_not_automount](http://wiki.sabayonlinux.org/index.php?title=HOWTO:_USB_pen_drive_will_not_automount)

---

