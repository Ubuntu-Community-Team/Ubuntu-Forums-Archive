---
title: "floppy unmountable, unreadable after edgy upgrade"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by bonjun on 2006-11-08
floppy unmountable, unreadable after edgy upgrade... 
it is working well with dapper, after the upgrade, not working anymore...

please help,

TIA

-------
edit:

my edgy is xubuntu

---

### Post by skunkydog on 2006-11-09
so you can't read any floppy disks or one in particular?

---

### Post by bonjun on 2006-11-09
sorry for the very late reply...........

yes, i can't,,,, but with previous version of ubuntu, it works well with me and floppy is readable/mountable in other pc

when i mount it using terminal it says:

> ~$ pmount /dev/fd0
mount: block device /dev/fd0 is write-protected, mounting read-only
mount: /dev/fd0: can't read superblock


---

### Post by skunkydog on 2006-11-09
you know, i'm not really sure.  after you get that message, do ```
dmesg
``` and see if there is any useful info in there, towards the bottom.  Also, try ```
sudo pmount /dev/fd0
``` in case it is a permissions thing.  Lastly, you can try ```
sudo mount /dev/fd0 /media/floppy
``` in case the error is specific to pmount.

---

### Post by bonjun on 2006-11-10
here's what i got

> dmesg

> [   72.181290] Floppy drive(s): fd0 is 1.44M
 at the bottom
> [ 1080.017599] end_request: I/O error, dev fd0, sector 0
[ 1118.222943] end_request: I/O error, dev fd0, sector 0
[ 1156.427649] end_request: I/O error, dev fd0, sector 0
[ 1194.608902] end_request: I/O error, dev fd0, sector 0
[ 1250.376159] end_request: I/O error, dev fd0, sector 0
[ 1288.569505] end_request: I/O error, dev fd0, sector 0
[ 1326.890754] end_request: I/O error, dev fd0, sector 0
[ 1365.092050] end_request: I/O error, dev fd0, sector 0
[ 1403.269294] end_request: I/O error, dev fd0, sector 0
[ 1403.269599] FAT: unable to read boot sector


> ~$ sudo pmount /dev/fd0
mount: block device /dev/fd0 is write-protected, mounting read-only
mount: /dev/fd0: can't read superblock

> ~$ sudo mount /dev/fd0 /media/floppy
mount: block device /dev/fd0 is write-protected, mounting read-only
mount: /dev/fd0: can't read superblock

---

### Post by bonjun on 2006-11-14
problem solved........... solution: fresh install edgy...

---

### Post by skunkydog on 2006-11-15
but that raises more questions than it answers!!!

but that's great

---

