---
title: "Unable to mount floppy"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by paddy1 on 2008-07-21
ZI can only access th floppy drive using rescan. I cannot open or save to. this is the error message

Cannot invoke CheckForMedia on HAL: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

_**:confused:**_

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d84aa9fe-5534-4ae6-8cbb-164caf4481be /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=cf28f0c9-34a3-457d-975f-4aba12928101 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Partyboi2 on 2008-07-23
There has been a [[COLOR=Blue]bug report [/COLOR]]("https://bugs.launchpad.net/gvfs/+bug/197954")opened for it, maybe you might be able to provide then with additional info.

---

