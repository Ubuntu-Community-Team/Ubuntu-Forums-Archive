---
title: "Help with broken automounting for flash drives"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by isagani on 2007-10-23
**Problem:**

After upgrading to gutsy, automounting of flashdrives / ipod / etc (stuff that don't reside in fstab but should be automounted) has stopped working for me. The error displayed is:

```
Cannot mount volume.
Unable to mount the volume 'FLASHDISK'.

Details:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program or other error. In some cases useful info is found in syslog - try dmesg | tail or so
```

**What I've done so far**

Reading related posts I found out that some people fixed this issue by removing the package hal. So I completely removed hal (through Synaptic). And reinstalled it. During the part where the hal is restarted the flash drive I have connected is suddenly automounted properly and can be accessed.

But once I remove it and plug it in again. I get exactly the same error as before.

**Other Info**

Even with this issue, I can manually mount the flashdrive / ipod, but I have to use sudo. There are issues when mounting as root (ex. amarok thinks you don't have permission to write to it if you're not root)

**Here's the dmesg | tail output**

```
50112.996000] usb-storage: device found at 7
[50112.996000] usb-storage: waiting for device to settle before scanning
[50117.996000] usb-storage: device scan complete
[50117.996000] scsi 7:0:0:0: Direct-Access     JetFlash TS2GJFV10        0.00 PQ: 0 ANSI: 2
[50117.996000] SCSI device sdb: 4030463 512-byte hdwr sectors (2064 MB)
[50117.996000] sdb: Write Protect is off
[50117.996000] sdb: Mode Sense: 00 00 00 00
[50117.996000] sdb: assuming drive cache: write through
[50118.000000] SCSI device sdb: 4030463 512-byte hdwr sectors (2064 MB)
[50118.000000] sdb: Write Protect is off
[50118.000000] sdb: Mode Sense: 00 00 00 00
[50118.000000] sdb: assuming drive cache: write through
[50118.000000]  sdb: sdb1
[50118.104000] sd 7:0:0:0: Attached scsi removable disk sdb
[50118.104000] sd 7:0:0:0: Attached scsi generic sg2 type 0
[50118.760000] FAT: Unrecognized mount option "usefree" or missing value
[50135.044000] TKIP: replay detected: STA=00:19:5b:e5:57:e6 previous TSC 000000000000 received TSC 000000000000
```

Any help on this would be much appreciated. Thanks :)

---

### Post by isagani on 2007-10-24
sorry to bump my own post, but I really need help.

---

