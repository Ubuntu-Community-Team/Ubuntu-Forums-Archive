---
title: "fstab oddity"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by AlanRogers on 2007-11-29
My machine is behaving a little oddly and I'm not sure why. Below is the content of my fstab file. ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=0aeeebbe-fe6c-4df0-b914-aa9a764e5fd8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=dc5683d7-8c3b-45b6-883c-ce98cd92d4fd /home           ext3    defaults        0       2
# /dev/hda3
UUID=10c429d6-12f2-4e50-85e6-82b45c712560 none            swap    sw              0       0
# /dev/hdb1
UUID=9989a8be-a786-423d-862b-9212a9ebb2fd /home/apr/home  ext3    defaults        0       2
# /dev/hdb2
UUID=2398705b-6f6d-476b-b380-bfcf874762cb /home/apr/work  ext3    defaults        0       2
# /dev/hdb3
UUID=b97982ce-8429-4120-9147-239af49d2e87 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```As you can see, the drives were originally installed as hda and hdb but are now commented out and are loaded by their UUIDs. The system appears to work ok but they appear in other utilities, such as GParted, as sda and sdb - they're definitely IDE drives.

Any ideas how this could have occurred, what the performance/stability implications are and how I could/should fix it?

---

### Post by scxtt on 2007-11-29
since feisty (maybe earlier?), all drives (sata/ide) are managed by libata, so they'll all be /dev/s* ... it makes it more of a "no brainer" to use the UUID (much more specific, doesn't really change) instead of the /dev path ...

i use LABEL myself.

---

### Post by Keith Hedger on 2007-11-29
The main problem with uuids is if you format your partition the uuid changes and u have to alter a bunch of system stuff like fstab and the grub menu, I had to do a reinstall from a backup and reformated my main partition and grub would no longer boot because the uuid had changed, it took a while to realize what the frick was going on!

---

