---
title: "Ubuntu Server 10.04 RAID 5 Grub2 boot issue"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by Koji-Murasame on 2010-05-18
I've been searching for a fix for this the past couple days with no success. I'm trying to install Ubuntu Server 10.04 with a software RAID 5 setup. The installation completes but when I attempt to boot I get an error "ALERT! /dev/disk/by-uuid/1323ce7f-5a88-44da-aeb5-93f7573b3871 does not exist. Dropping to a shell!" I've tried editing the commands inside the Grub editing screen with no success and getting either the same error or "No init found. Try passing init= bootarg."

Contents of Grub2 editing screen:
```
recordfail
insmod raid
insmod raid5rec
insmod mdraid
insmod ext2
setroot='(md0)'
search --no-floppy --fs-uuid --set 1323ce7f-5a88-44da-aeb5-93f7573b3871
linux /boot/vmlinuz-2.6.32-21-server root=UUID=1323ce7f-5a88-44da-aeb5-93f7573b3871 ro   quiet
initrd /boot/initrd.img-2.6.32-21-server
```

I tried removing the search string with no success. I tried changing the device address from UUID to its actual /dev path also without success. I'd appreciate some insight and maybe a point in the right direction.

---

### Post by jonnycat27 on 2010-07-28
I am having the same issue with a software RAID 1 setup. Any fix for this besides reinstalling?

---

### Post by shirsch on 2010-08-30
> **Koji-Murasame said:**
> I've been searching for a fix for this the past couple days with no success. I'm trying to install Ubuntu Server 10.04 with a software RAID 5 setup. The installation completes but when I attempt to boot I get an error "ALERT! /dev/disk/by-uuid/1323ce7f-5a88-44da-aeb5-93f7573b3871 does not exist. Dropping to a shell!" I've tried editing the commands inside the Grub editing screen with no success and getting either the same error or "No init found. Try passing init= bootarg."

Contents of Grub2 editing screen:
```
recordfail
insmod raid
insmod raid5rec
insmod mdraid
insmod ext2
setroot='(md0)'
search --no-floppy --fs-uuid --set 1323ce7f-5a88-44da-aeb5-93f7573b3871
linux /boot/vmlinuz-2.6.32-21-server root=UUID=1323ce7f-5a88-44da-aeb5-93f7573b3871 ro   quiet
initrd /boot/initrd.img-2.6.32-21-server
```

I tried removing the search string with no success. I tried changing the device address from UUID to its actual /dev path also without success. I'd appreciate some insight and maybe a point in the right direction.

Make sure your RAID install is using a "version 0.90" metatdata superblock.  Check this with "mdadm -Q --detail /dev/md0".  If you're using 1.x, grub2 support for that was introduced to the CVS head in late July 2010.  Ubuntu source packages of the cutting-edge code are available for 10.10 Beta, but can made to build on 10.04 with a modest amount of hair-pulling.

---

