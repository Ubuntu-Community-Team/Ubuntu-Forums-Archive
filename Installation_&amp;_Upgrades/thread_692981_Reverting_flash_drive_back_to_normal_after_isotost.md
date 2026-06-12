---
title: "Reverting flash drive back to normal after isotostick"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by dravidan on 2008-02-10
I was able to successfully install Gutsy using the following thread.

[http://ubuntuforums.org/showthread.php?t=405008&highlight=isotostick](http://ubuntuforums.org/showthread.php?t=405008&highlight=isotostick)

Now my problem is I can not mount the flash drive anymore on the newly installed gutsy box.  Everytime, I stick in the drive I get a pop-up that says:  
"Cannot mount volume.  Invalid mount option when attempting to mount the volume."

dmesg command shows:

[  914.964000] usb 1-7: USB disconnect, address 4
[  918.624000] usb 1-7: new full speed USB device using ohci_hcd and address 5
[  918.836000] usb 1-7: configuration #1 chosen from 1 choice
[  918.836000] scsi5 : SCSI emulation for USB Mass Storage devices
[  918.836000] usb-storage: device found at 5
[  918.836000] usb-storage: waiting for device to settle before scanning
[  923.840000] usb-storage: device scan complete
[  923.848000] scsi 5:0:0:0: Direct-Access     Generic  USB SD Reader    2.00 PQ: 0 ANSI: 0
[  923.956000] sd 5:0:0:0: [sdb] 3970048 512-byte hardware sectors (2033 MB)
[  923.972000] sd 5:0:0:0: [sdb] Write Protect is off
[  923.972000] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  923.972000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  923.996000] sd 5:0:0:0: [sdb] 3970048 512-byte hardware sectors (2033 MB)
[  924.008000] sd 5:0:0:0: [sdb] Write Protect is off
[  924.008000] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  924.008000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  924.008000]  sdb: sdb1
[  924.020000] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  924.020000] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  924.956000] UDF-fs: No VRS found
[  925.552000] Unable to identify CD-ROM format.

It appears that when I used this drive to install gutsy using isotostick something changed it to emulate as a CDROM.  I need help reverting back as a normal flash drive.  I am able to see the contents on my other ubuntu box and windows box but can not format the drive.

---

### Post by dravidan on 2008-02-10
I apologize, I didn't do enough searching to find out if it happened to others.  The solutions is: remove the line for your /dev/sdb* on your /etc/fstab file.

---

### Post by dravidan on 2008-02-10
[http://ubuntuforums.org/showthread.php?t=591012&highlight=isotostick](http://ubuntuforums.org/showthread.php?t=591012&highlight=isotostick)

---

