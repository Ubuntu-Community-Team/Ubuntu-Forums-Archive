---
title: "Dell Latitude C600 CD Mount Help!!"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by Snookieboy on 2007-05-29
Hi there I am running 7.04 with my Dell Latitude c600 laptop and I am having problems "mounting" my CD ROM Drive It says "Unable To Mount Volume" whenever I double click it.

This is after a fresh install which was from a CD in this very drive so it does work :\

If anyone could help, that would be great :)

my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=67199447-752f-4584-8008-2fdaab70d9eb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=78441ea5-e90b-447b-8b19-45a409ebd9f1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by wolfsandwich on 2007-08-03
me too!  same laptop, same 7.04, same problem.  i'm pretty sure my cdrw/dvd is good, i was using it not long ago with 6.06 on the same machine (different hard drive).


my fstab:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=19d4a54c-8610-4b1f-b97a-bc9d478c7827 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=98b5d8ea-fd63-4027-925a-cb7b1dc78ad6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0






any help would be great, i really need to be able to use all of that stuff.

thanks.

---

### Post by wolfsandwich on 2007-08-11
i replaced the drive.  now everything is good again.  old pets back from the dead and everything.  

thanks.

---

