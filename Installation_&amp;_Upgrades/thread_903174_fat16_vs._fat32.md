---
title: "fat16 vs. fat32"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-08-28
I got two flash drives, my old one 128 MB (still working ;-) ) is fat16, while my new one 8 GB is a fat32.

Plugging in 128MB (fat16) automounts the drive, while 8GB (fat32) doesn't.

How can I get both to automount?

bye

R.

---

### Post by _sebastian_ on 2008-08-28
AFAIK both should mount automatically. I can't think of a real reason for auto mounting one and not the other.

Have you checkd the fstab, or you log files? There might be a file system issue during mount. 
Else no idea, sorry

---

### Post by ELMIT on 2008-08-28
my /var/log/messages says:

1. 8GB (fat32):
> Aug 28 18:59:44 ronald-desktop kernel: [172880.050272] usb 2-5.1: new high speed USB device using ehci_hcd and address 13
Aug 28 18:59:44 ronald-desktop kernel: [172880.105621] usb 2-5.1: configuration #1 chosen from 1 choice
Aug 28 18:59:44 ronald-desktop kernel: [172880.148904] scsi5 : SCSI emulation for USB Mass Storage devices
Aug 28 18:59:52 ronald-desktop kernel: [172885.660890] scsi 5:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  1.00 PQ: 0 ANSI: 2
Aug 28 18:59:52 ronald-desktop kernel: [172885.671107] sd 5:0:0:0: [sde] 15859712 512-byte hardware sectors (8120 MB)
Aug 28 18:59:52 ronald-desktop kernel: [172885.674192] sd 5:0:0:0: [sde] Write Protect is off
Aug 28 18:59:52 ronald-desktop kernel: [172885.682790] sd 5:0:0:0: [sde] 15859712 512-byte hardware sectors (8120 MB)
Aug 28 18:59:52 ronald-desktop kernel: [172885.684840] sd 5:0:0:0: [sde] Write Protect is off
Aug 28 18:59:52 ronald-desktop kernel: [172885.684854]  sde: sde1
Aug 28 18:59:52 ronald-desktop kernel: [172885.687381] sd 5:0:0:0: [sde] Attached SCSI removable disk
Aug 28 18:59:52 ronald-desktop kernel: [172885.687427] sd 5:0:0:0: Attached scsi generic sg5 type 0


no automount!

2. 128MB (fat16):
> Aug 28 19:03:50 ronald-desktop kernel: [173072.383770] usb 2-5.1: new high speed USB device using ehci_hcd and address 14
Aug 28 19:03:50 ronald-desktop kernel: [173072.497655] usb 2-5.1: configuration #1 chosen from 1 choice
Aug 28 19:03:50 ronald-desktop kernel: [173072.528649] scsi6 : SCSI emulation for USB Mass Storage devices
Aug 28 19:03:55 ronald-desktop kernel: [173077.379587] scsi 6:0:0:0: Direct-Access     C-ONE    128MB Tiny       2.00 PQ: 0 ANSI: 2
Aug 28 19:03:55 ronald-desktop kernel: [173077.437916] sd 6:0:0:0: [sde] 256000 512-byte hardware sectors (131 MB)
Aug 28 19:03:55 ronald-desktop kernel: [173077.440494] sd 6:0:0:0: [sde] Write Protect is off
Aug 28 19:03:55 ronald-desktop kernel: [173077.449603] sd 6:0:0:0: [sde] 256000 512-byte hardware sectors (131 MB)
Aug 28 19:03:55 ronald-desktop kernel: [173077.452075] sd 6:0:0:0: [sde] Write Protect is off
Aug 28 19:03:55 ronald-desktop kernel: [173077.452089]  sde: sde1
Aug 28 19:03:55 ronald-desktop kernel: [173077.454649] sd 6:0:0:0: [sde] Attached SCSI removable disk
Aug 28 19:03:55 ronald-desktop kernel: [173077.454687] sd 6:0:0:0: Attached scsi generic sg5 type 0


/etc/fstab:
>  cat /etc/fstab

proc /proc proc defaults 0 0
/dev/mapper/lvmvolume-root / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hdb1 :
UUID=df0e768b-fee6-4f1a-b3da-ed8025f4230b /boot ext3 defaults 0 2
/dev/mapper/lvmvolume-home /home ext3 defaults 0 2
# Entry for /dev/hdc1 :
UUID=520407AE0407945F /media/hdc1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hdd1 :
UUID=F0A4B9EBA4B9B486 /media/hdd1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hdc7 :
UUID=aeefe374-0e0f-4213-a439-66b7eb8bb3d1 none swap sw 0 0
/dev/mapper/lvmvolume-swap none swap sw 0 0
/dev/hdc7 none swap sw 0 0
#/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0


Drive directory pops up! (Automounted)


Any ideas?

bye

R.

---

### Post by Pumalite on 2008-08-28
Check the Fat32 with recuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
(TestDisk)
Particularly the first 512 bytes

---

### Post by ELMIT on 2008-08-28
I have no idea what you try to suggest me to do with that !!!

bye

R.

---

### Post by revertex on 2008-10-03
Maybe there is something with gnome-volume-manager.

Does something show in /media when you plug both drivers?
Maybe it's mounted but not open automatically.

Automount there is nothing to do with fstab.

Testdisk have no use if your flash drive work fine if inserted alone.

It's far from a easy solution, nor the proper solution, maybe a workaround, but works very well.
IMHO writing udev rules is far superior than the whole automount thingy.

I use this in my desktop to mount my camera, mobile, usbdrive, mp3 player, and in several headless servers to automount a external usb HD.

[http://ubuntuforums.org/showthread.php?t=339178](http://ubuntuforums.org/showthread.php?t=339178)

more details and examples here:
[http://www.reactivated.net/writing_udev_rules.html#example-usbhdd](http://www.reactivated.net/writing_udev_rules.html#example-usbhdd)

---

