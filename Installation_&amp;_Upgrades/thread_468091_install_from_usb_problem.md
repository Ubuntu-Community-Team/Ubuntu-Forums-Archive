---
title: "install from usb problem"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by Saxis on 2007-06-08
I'm trying to install from a 1gb USB pen drive on a Fujitsu Lifebook B6110D.  I've done this successfully before with Edgy with [these]("https://help.ubuntu.com/community/Installation/FromUSBStick") instructions, but now I'm trying to do it with Feisty, and having trouble mounting it to /cdrom.  I checked dmesg and it is showing my usb drive as sdb1, but when I try to mount -t vfat /dev/sdb1 /cdrom it returns failed: No such device.  Any ideas?

---

### Post by Saxis on 2007-06-08
I reformatted my pen drive and set it up again and I still get the same message. It boots fine, and when it complains about the missing cdrom, I enter the console and look at dmesg, which shows:

> usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete
scsi 3:0:0:0: Direct-Access     USB2.0     Flash Disk     2.00 PQ: 0 ANSI: 2
ready
SCSI device sdb: 2048000 512-byte hdwr sectors (1049 MB)
sdb: Write Protect is off
sdb: Mode Sense: 03 00 00 00
sdb: assuming drive cache: write through
SCSI device sdb: 2048000 512-byte hdwr sectors (1049 MB)
sdb: Write Protect is off
sdb: Mode Sense: 03 00 00 00
sdb: assuming drive cache: write through
 sdb: sdb1
sd 3:0:0:0: Attached scsi removable disk sdb
sd 3:0:0:0: Attached scsi generic sg1 type 0

Ok, so it looks all good to me, but: 

> # mount -t vfat /dev/sdb1 /cdrom
# mount: Mounting /dev/sdb1 on /cdrom failed: No such device

How is this possible? I tried it on another model of Fujitsu and it does the exact same thing.  I remember when I did this on Edgy, it came up as sda1, and booted/installed just fine.

---

### Post by Saxis on 2007-06-08
I found my old Edgy iso and copied that to my pen drive, copied the necessary folders to the root, made the changes in the sysconfig, and bam, works like a charm!  The usb device is still detected as sda1 in Edgy... not sure why it would be sdb1 in Feisty, but it wasn't working either way.  Even in Edgy, I got the "determining codename" error, and edited the db_get line in /usr/share/debconf/confmodule to read like this:

> db_get() {
  _db_cmd "GET $@"
  if ! [ "$RET" ] ; then
    RET="edgy"
  fi
}

Now it is finally doing the install... I guess I'll just have to upgrade to Feisty after.

---

### Post by mountaindude1 on 2007-09-05
Having same problems, both with Xubuntu 6.06.1 Alternate and Xubuntu 7.04 Alternate.
Anyone found a reason for/solution to the problem?

/MD

---

### Post by scapalexis888 on 2007-09-20
I also have the same problem. I can't mount my PNY 1gb flash drive as a cdrom. I switched to a 2gb SanDisk Cruzer and that didnt even boot. I think the main reason for this trouble is the combination of your mobo and the flash drive. Try different combos and see what works. Thats what i am doing and i am still on the search for the right combo.

---

