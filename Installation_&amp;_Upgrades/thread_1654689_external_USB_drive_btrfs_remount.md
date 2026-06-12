---
title: "external USB drive btrfs remount"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by anystupidname1 on 2010-12-28
I'm running Maverick on an older Stinkpad. I have a btrfs /home as a second partition on the internal HDD and a brand shiny new 3TB external USB western digital drive also formatted btrfs. I'm having a problem whenever I hibernate/suspend the laptop by closing the lid and start it back up later, the external drive won't remount unless I do a complete reboot. I have no entry in /etc/fstab for the external drive.

> Unable to mount "blah" DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

---

### Post by bapoumba on 2010-12-30
[http://ubuntuforums.org/showthread.php?t=1175638](http://ubuntuforums.org/showthread.php?t=1175638)
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/355522](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/355522)

Maybe..

---

### Post by anystupidname1 on 2010-12-30
Yes, I read those before posting. Thanks anyway...

First link has multiple off the wall answers that don't work and the bug was fixed several versions ago.

---

### Post by anystupidname1 on 2011-01-05
:-k bump

---

