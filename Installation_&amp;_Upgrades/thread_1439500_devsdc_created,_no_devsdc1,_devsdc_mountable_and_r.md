---
title: "/dev/sdc created, no /dev/sdc1, /dev/sdc mountable and readable"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by marcchehab on 2010-03-26
Ladies and Gentlemen

I have a weird behaviour here on Ubuntu 10.04 with my Sony PRS-600 ereader. The device worked on Ubuntu 9.10 and still does on Windows, so it must be my system. The internal memory isnt conveniently automounted anymore. 

Ubuntu creates a device /dev/sdc, but no /dev/sdc1. I can mount /dev/sdc and access the data properly. A behaviour I personally haven't ever seen :). This is the extract from a mount:
/dev/sdc on /home/marc/test type vfat (rw)

There are also two card readers in the device (sdd and sdf). Here's my dmesg. 

```
[ 1202.948065] usb 1-6: new high speed USB device using ehci_hcd and address 3
[ 1203.097415] usb 1-6: configuration #1 chosen from 2 choices
[ 1203.127591] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1203.131861] usb-storage: device found at 3
[ 1203.131865] usb-storage: waiting for device to settle before scanning
[ 1208.129505] usb-storage: device scan complete
[ 1208.130412] scsi 3:0:0:0: Direct-Access     Sony     PRS-600          1.00 PQ: 0 ANSI: 2
[ 1208.132655] scsi 3:0:0:1: Direct-Access     Sony     PRS-600 MS       1.00 PQ: 0 ANSI: 2
[ 1208.137287] scsi 3:0:0:2: Direct-Access     Sony     PRS-600 SD       1.00 PQ: 0 ANSI: 2
[ 1208.137771] scsi 3:0:0:3: Direct-Access     Sony     PRS-600 Launcher 1.00 PQ: 0 ANSI: 2
[ 1208.143871] sd 3:0:0:0: Attached scsi generic sg3 type 0
[ 1208.146087] sd 3:0:0:1: Attached scsi generic sg4 type 0
[ 1208.147284] sd 3:0:0:2: Attached scsi generic sg5 type 0
[ 1208.148747] sd 3:0:0:3: Attached scsi generic sg6 type 0
[ 1208.168112] sd 3:0:0:0: [sdc] 802560 512-byte logical blocks: (410 MB/391 MiB)
[ 1208.278142] sd 3:0:0:0: [sdc] Write Protect is off
[ 1208.278156] sd 3:0:0:0: [sdc] Mode Sense: 0f 00 00 00
[ 1208.278165] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[ 1208.295361] sd 3:0:0:2: [sde] Attached SCSI removable disk
[ 1208.301377] sd 3:0:0:1: [sdd] 3928064 512-byte logical blocks: (2.01 GB/1.87 GiB)
[ 1208.303374] sd 3:0:0:3: [sdf] 20480 512-byte logical blocks: (10.4 MB/10.0 MiB)
[ 1208.408143] sd 3:0:0:1: [sdd] Write Protect is off
[ 1208.408157] sd 3:0:0:1: [sdd] Mode Sense: 0f 00 00 00
[ 1208.408165] sd 3:0:0:1: [sdd] Assuming drive cache: write through
[ 1208.518153] sd 3:0:0:3: [sdf] Write Protect is on
[ 1208.518167] sd 3:0:0:3: [sdf] Mode Sense: 0f 00 80 00
[ 1208.518176] sd 3:0:0:3: [sdf] Assuming drive cache: write through
[ 1208.638278] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[ 1208.638296]  sdc:
[ 1208.778147] sd 3:0:0:1: [sdd] Assuming drive cache: write through
[ 1208.778164]  sdd:
[ 1208.888162] sd 3:0:0:3: [sdf] Assuming drive cache: write through
[ 1208.888180]  sdf: sdd1
[ 1208.903810] 
[ 1209.018165] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[ 1209.018181] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[ 1209.148175] sd 3:0:0:1: [sdd] Assuming drive cache: write through
[ 1209.148192] sd 3:0:0:1: [sdd] Attached SCSI removable disk
[ 1209.258351] sd 3:0:0:3: [sdf] Assuming drive cache: write through
[ 1209.258366] sd 3:0:0:3: [sdf] Attached SCSI removable disk

```

I reckon once I get it back to create a normal /dev/sdc1 again, I get back the normal behaviour. Ou yes, gparted and fdisk show me no partitions at all.

if you need any more info, please, Im happy to provide it.

cheers!

---

### Post by andrewc6l on 2010-03-26
If you can mount /dev/sdc, that means that you have a real file system on /dev/sdc (in other words, there's no partition table). This is perfectly legal, but not usual anymore. (It used to be a lot more common back when we were using /dev/fd0 to access the floppy drive!)

If you want, you can:
 - mount /dev/sdc
 - copy the data off /dev/sdc
 - umount /dev/sdc
 - fdisk /dev/sdc and create a partition (which will show up as /dev/sdc1) ***
 - use mkfs /dev/sdc1 to build a new filesystem of the type you choose on the partition ***
 - mount /dev/sdc1 and copy the data back

*** Be very careful in these steps - typos (eg /dev/sda instead of /dev/sdc) can potentially make your machine non-bootable. Make *sure* you're changing the right drive!

You'll lose a tiny bit of storage - right now your file system is using all the space on the drive. A partition table takes up a little room.

---

