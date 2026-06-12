---
title: "lilo error after upgrading from hoary to breezy"
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by timozilla on 2006-02-20
I keep getting this error when ever I run lilo -v

Warning: '/proc/partitions' does not match '/dev' directory structure.
Name change: '/dev/dm-0' -> '/dev/dm'
device-mapper ioctl cmd 12 failed: No such device or address
Fatal: device-mapper: dm_task_run(DM_DEVICE_TABLE) failed

Lilo is at /dev/hda1 and using lvm.

What can I do. to fix it

Timozilla

---

### Post by Morpheus4you on 2007-07-23
> **timozilla said:**
> I keep getting this error when ever I run lilo -v

Warning: '/proc/partitions' does not match '/dev' directory structure.
Name change: '/dev/dm-0' -> '/dev/dm'
device-mapper ioctl cmd 12 failed: No such device or address
Fatal: device-mapper: dm_task_run(DM_DEVICE_TABLE) failed

Lilo is at /dev/hda1 and using lvm.

What can I do. to fix it

Timozilla

It seems i have the same problem. The error i get after running "lilo -v" is:

```

LILO version 22.6.1, Copyright (C) 1992-1998 Werner Almesberger
Development beyond version 21 Copyright (C) 1999-2004 John Coffman
Released 17-Nov-2004, and compiled at 09:45:15 on May 11 2006
Ubuntu

Warning: LBA32 addressing assumed
Reading boot sector from /dev/hde
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/dm'
    Name change: '/dev/dm-1' -> '/dev/.static/dev/mapper/VolGroup00-LogVol02'
    Name change: '/dev/dm-2' -> '/dev/.static/dev/mapper/VolGroup00-LogVol05'
    Name change: '/dev/dm-3' -> '/dev/.static/dev/mapper/VolGroup00-LogVol04'
    Name change: '/dev/dm-4' -> '/dev/.static/dev/mapper/VolGroup00-LogVol03'
    Name change: '/dev/dm-5' -> '/dev/.static/dev/mapper/VolGroup00-LogVol00'
    Name change: '/dev/dm-6' -> '/dev/.static/dev/mapper/VolGroup01-LogVol01'
    Name change: '/dev/dm-7' -> '/dev/.static/dev/mapper/VolGroup01-LogVol00'
    Name change: '/dev/dm-8' -> '/dev/evms/hde1'
    Name change: '/dev/dm-9' -> '/dev/evms/.nodes/hde2'
    Name change: '/dev/dm-10' -> '/dev/evms/lvm2/VolGroup00/LogVol00'
    Name change: '/dev/dm-11' -> '/dev/evms/lvm2/VolGroup00/LogVol01'
    Name change: '/dev/dm-12' -> '/dev/evms/lvm2/VolGroup00/LogVol02'
    Name change: '/dev/dm-13' -> '/dev/evms/lvm2/VolGroup00/LogVol03'
    Name change: '/dev/dm-14' -> '/dev/evms/lvm2/VolGroup00/LogVol04'
    Name change: '/dev/dm-15' -> '/dev/evms/lvm2/VolGroup00/LogVol05'
    Name change: '/dev/dm-16' -> '/dev/evms/.nodes/hdg1'
    Name change: '/dev/dm-17' -> '/dev/evms/lvm2/VolGroup01/LogVol00'
    Name change: '/dev/dm-18' -> '/dev/evms/lvm2/VolGroup01/LogVol01'
device-mapper: table ioctl failed: No such device or address
Fatal: device-mapper: dm_task_run(DM_DEVICE_TABLE) failed

```

I have a clean install of Ubuntu (using ubuntu-6.06.1-server-i386.iso)
-My lilo version is 22.6.1
-uname -a outputs: "Linux SERVERVELP 2.6.15-28-server #1 SMP Thu May 10 10:40:27 UTC 2007 i686 GNU/Linux"

I use lvm and have a /boot folder on my ext3 formatted root disk (so no separate partition for /boot).

Could it help if i installed grub? This one really makes me desperate.

---

