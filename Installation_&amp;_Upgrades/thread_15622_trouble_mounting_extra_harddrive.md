---
title: "trouble mounting extra harddrive"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by wildealien on 2005-02-15
finally made the switch from Fedora to Ubuntu.  everything seems to be working good so far!

however, i'm trying to add an automount to fstab.  Ubuntu is currently running on a partition on a 13gig drive.  i have been able to access another partition on this drive running win98se just fine.  however, i can't seem to mount my separate 80gig harddrive.

here is the line which seems to work well with the win98se partition:
*/dev/hda1	/mnt/win98se	vfat	ro,auto,uid=1000	0	0*

here is the line for the 80gig drive:
*/dev/hdb1	/mnt/80gig	vfat	ro,auto,uid=1000	0	0*

...which gives me an error:
[I]mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       or too many mounted file systems[/I]

i'm sure that the drive has a vfat formatting, since i formatted it in windows, and was once able to access/read/write to it under win98se.  the 80gig drive has data on it, so i'd rather not reformat it.

now, when i run:
*$ sudo fdisk -l*

i get:
[I]   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1023     8217243   55  EZ-Drive[/I]

however, using EZ-Drive as my filesystem type gives:
*mount: fs type EZ-Drive not supported by kernel*

any ideas?
thanks!



noteable:  upon first getting the 80gig drive, win98se couldn't use it either, until i installed/ran the software that came with it, to help the old OS recognize the drive (WesternDigital Lifeguard Tools).  the drive is a WesternDigital.

---

### Post by wildealien on 2005-02-15
i've done some reading up on this EZ-Drive business, and it seems to be a little program that is put into the BIOS for old motherboards like mine that have trouble reading large hard drives.

anyone know how to get rid of it?  :)

---

### Post by wildealien on 2005-02-16
[QUOTE=wildealien]i've done some reading up on this EZ-Drive business, and it seems to be a little program that is put into the BIOS for old motherboards like mine that have trouble reading large hard drives.

anyone know how to get rid of it?  :)[/QUOTE]
 anyone?

bueller?  bueller?

---

