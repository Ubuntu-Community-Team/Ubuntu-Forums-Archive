---
title: "No /home partition after upgrade?"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by maxol on 2008-04-28
I've just upgraded Xubuntu from 7.10 to 8.04 and on reboot at login I get a prompt telling me my home directory does not appear to exist.

It does exist on a seperate partition where its been since Breezy. I've booted up a live CD and fsck'd my root and home partitions and had a look to see if my fstab is pointing to the right places and everything seems well.

Any ideas why hardy should get its knickers in a twist over a seperate home partition?

This is on an old Dell Latitude C610 running 32bit Xubuntu.

---

### Post by mikewhatever on 2008-04-28
Why don't you post your fstab so that others may take a second glance.

---

### Post by maxol on 2008-04-28
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=6b211862-fc0d-4de9-8897-31d58f22e10c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=3a54122f-b23c-4bdb-8e33-e309bb0f98fa /home           ext3    defaults        0       2
# /dev/hda5
UUID=ee9cc903-a9f3-427f-bc5a-bed958258401 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

192.168.1.90:/home /home/max/shiny nfs rsize=8192,wsize=8192,timeo=14,intr

---

### Post by jpryor68 on 2008-04-29
Are you sure it's the /home i.e /dev/hda3, which the message says doesn't exist? Not the 192.168.1.90:/home directory? Try commenting out the last (nfs) line of your fstab and seeing whether you can login then.

---

### Post by jpryor68 on 2008-04-29
Also, I doubt that this is valid:

/dev/ /media/floppy0 auto rw,user,noauto 0 0

Shouldn't the first item be /dev/whatever_your_floppy_device_is,
not just /dev/  ?

---

### Post by maxol on 2008-04-29
Thanks for the input but I've done a fresh install from disc which works fine.

---

