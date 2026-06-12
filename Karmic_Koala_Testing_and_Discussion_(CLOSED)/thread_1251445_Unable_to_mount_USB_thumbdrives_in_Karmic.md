---
title: "Unable to mount USB thumbdrives in Karmic"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andresmh on 2009-08-27
I get something like this:
[IMG]http://dl.getdropbox.com/u/285483/tmp/screenshot34.png[/IMG]

So I ran: dmesg | tail and I got this
```
[   54.657705] Initializing USB Mass Storage driver...
[   54.660163] scsi5 : SCSI emulation for USB Mass Storage devices
[   54.660439] usbcore: registered new interface driver usb-storage
[   54.660445] USB Mass Storage support registered.
[   54.663344] usb-storage: device found at 5
[   54.663348] usb-storage: waiting for device to settle before scanning
[   59.661441] usb-storage: device scan complete
[   59.662684] scsi 5:0:0:0: Direct-Access     USB 2.0  Flash Disk       1100 PQ: 0 ANSI: 0 CCS
[   59.663341] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   59.677769] sd 5:0:0:0: [sdb] 3963904 512-byte logical blocks: (2.02 GB/1.88 GiB)
[   59.678635] sd 5:0:0:0: [sdb] Write Protect is off
[   59.678640] sd 5:0:0:0: [sdb] Mode Sense: 43 00 00 00
[   59.678645] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   59.682640] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   59.682649]  sdb: sdb1
[   59.751543] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   59.751550] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   60.280333] UDF-fs: No VRS found
[   60.280340] UDF-fs: Rescanning with blocksize 2048
[   60.363511] UDF-fs: No VRS found
[   60.363516] UDF-fs: No partition found (1)
[   60.417920] ISOFS: Unable to identify CD-ROM format.
```

Any ideas?

---

### Post by hgergo on 2009-08-27
This was my problem too ;)

[http://ubuntuforums.org/showthread.php?t=1250571](http://ubuntuforums.org/showthread.php?t=1250571)

simpli make a folder in media then  mount /dev/sd* /media/foldername


*=number of sd if you have one by me was sdb1

---

### Post by zoomy942 on 2009-08-27
mine is all of a sudden doing this too

---

### Post by andresmh on 2009-08-27
While it might be possible to do it manually it should be done automatically as it used to happen in Jaunty.

---

### Post by taavikko on 2009-08-28
Does this happen with a new user as well?

nautilus mounts USB-stick normally here.

Obtaining some debug info
unplug the USB-stick
```
devkit-disks --monitor
```
Insert USB-stick -> any output?

---

### Post by hgergo on 2009-08-28
This is apearing

added:     /org/freedesktop/DeviceKit/Disks/devices/sdb
added:     /org/freedesktop/DeviceKit/Disks/devices/sdb1
job-changed: /org/freedesktop/DeviceKit/Disks/devices/sdb1
job-changed: /org/freedesktop/DeviceKit/Disks/devices/sdb1


and then the error msg on the screen

---

### Post by NCLI on 2009-08-28
Probably a DeviceKit bug, anyone added a bug report yet?

---

### Post by zoomy942 on 2009-09-07
Well, an update this morning broke this again

---

