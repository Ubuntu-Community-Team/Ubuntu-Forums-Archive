---
title: "Unformatted USB drive not recognized after upgrade?"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by alp3t on 2007-10-21
Hi all,

I've had a bit of an issue with my upgrade to Gutsy.  I have an external drive (USB 2) which I use to try out new file systems.  I haven't had any trouble using Fiesty for this - even without an file system on the drive, it recognizes it, assigns it a SCSI device, and I can format it.  With Gusty, however, it detects the drive, (i.e. I can see it in the Device Manager dealy, and on the proc filesystem, right where it belongs), but Gusty hasn't given it a block device, so far as I can tell, and so I can't format it.  For what it's worth, if I plug another, formatted, USB drive in, it works fine.  Also, I've tried the unformatted USB drive on another machine with Feisty, and that still works fine, so the drive's not bad...

I caught the 'dmesg' output from plugging in the device, and here's what it says:

usb 3-3: new high speed USB device using ehci_hcd and address 9
usb 3-3: configuration #1 chosen from 1 choice
scsi3 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 9
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete

Any ideas?  

Thanks very much,

-Andrew

---

### Post by hlmuller on 2007-10-21
I'm clueless.  But you can try running ```
$ lsusb
```To see if the usb subsystem see's it.

Most usb mass storage devices are of the /dev/sd? variety.  I have seen /dev/sg? usb devices also.  You might try running ```
$ ls /dev/sd*
ls /dev/sg*
```after you run the first.

---

### Post by alp3t on 2007-10-21
hlmuller,

Thanks for the quick response!  Unfortunately, lsusb doesn't seem to find it, and there's no sd or sg drives in the dev directory, so it's not being picked up there.  For what it's worth, I found the dmesg output for the drive when it's added to the system that it *does* work with, and it's basically the same as on the non-functional system, but then with more messages about setting things up, etc:

[90853.208000] usb 4-4: new high speed USB device using ehci_hcd and address 3
[90853.340000] usb 4-4: configuration #1 chosen from 1 choice
[90853.340000] scsi3 : SCSI emulation for USB Mass Storage devices
[90853.340000] usb-storage: device found at 3
[90853.340000] usb-storage: waiting for device to settle before scanning
[90858.340000] usb-storage: device scan complete
[90864.344000] scsi 3:0:0:0: Direct-Access     External Disk 0                PQ: 0 ANSI: 2
[90864.344000] SCSI device sdb: 976773169 512-byte hdwr sectors (500108 MB)
[90864.344000] sdb: Write Protect is off
[90864.344000] sdb: Mode Sense: 1a 0c 00 00
[90864.344000] sdb: assuming drive cache: write through
[90864.348000] SCSI device sdb: 976773169 512-byte hdwr sectors (500108 MB)
[90864.348000] sdb: Write Protect is off
[90864.348000] sdb: Mode Sense: 1a 0c 00 00
[90864.348000] sdb: assuming drive cache: write through
[90864.348000]  sdb: unknown partition table
[90864.412000] sd 3:0:0:0: Attached scsi disk sdb
[90864.412000] sd 3:0:0:0: Attached scsi generic sg2 type 0

Any ideas as to what is missing between the scanning complete step and the "I know it's an external drive that I should assign a device to" step? :)

Thanks again!

-Andrew

---

