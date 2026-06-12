---
title: "mount + fstab question"
date: 2005-02-23
forum: Installation &amp; Upgrades
---

### Post by konan on 2005-02-23
Hi!
I edit my fstab that way, that my windows partitions (2) get mouneted at boot...
But ubuntu automatically makes shortcuts to this two partitions on my desktop and I don't like that... Iprefer to have my desktop with no shortcuts.
Is there any chance to make this two shortcuts dissapeare?

Thanx for any replay...

---

### Post by konan on 2005-02-23
Here's my fstab file:

[PHP]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda2	/media/windows	ntfs	umask=0222	0	0
/dev/hda5	/media/windows_sys	vfat	umask=000	0	0

[/PHP]

---

### Post by alastair on 2005-02-23
I don't know how to do this - never seen it.

I'd probably first try just deleting the shortcuts. Close everything I don't want started at login, and logout - "save session". Then login and see if they have gone. A guess though.

---

### Post by zcox on 2005-02-23
[QUOTE=konan]Hi!
I edit my fstab that way, that my windows partitions (2) get mouneted at boot...
But ubuntu automatically makes shortcuts to this two partitions on my desktop and I don't like that... Iprefer to have my desktop with no shortcuts.
Is there any chance to make this two shortcuts dissapeare?

Thanx for any replay...[/QUOTE]

Go to Applications --> System Tools --> Configuration Editor.

Then go /apps/nautilus/desktop and uncheck the volumes_visible checkbox.  That should do it.  If not then hopefully someone else knows.   :wink:

---

### Post by konan on 2005-02-24
**Thanx for second idea!**
I'll try it when i'll come home from work...

I tryed to delete them, but it's not possible... [-X

---

