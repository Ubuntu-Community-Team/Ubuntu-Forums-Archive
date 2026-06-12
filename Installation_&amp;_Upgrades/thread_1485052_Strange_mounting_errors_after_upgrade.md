---
title: "Strange mounting errors after upgrade"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by gweinstein on 2010-05-16
I upgraded a linux box from Koala to Lucid, and everything seems ok except at boot I **occasionally** get an error mounting some partitions.  Here is the boot.log:

```
fsck from util-linux-ng 2.17.2
/dev/sdb1: clean, 316325/17965056 files, 5723474/71844680 blocks
udevd[402]: can not read '/etc/udev/rules.d/z80_user.rules'


mount: /dev/sdb1 already mounted or /backup busy
mount: according to mtab, /dev/sdb1 is mounted on /
mountall: mount /backup [704] terminated with status 32
mountall: Filesystem could not be mounted: /backup
Skipping /backup at user request
Skipping /local at user request
 * Starting AppArmor profiles       [80G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

[74G[ OK ]
Not starting as we're not running in a vm.
 * Setting sensors limits       [80G 
[74G[ OK ]
 * Starting the Firestarter firewall...       [80G 
[74G[[31mfail[39;49m]

```

And here is the output from fdisk -l:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ea435

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        9729    78140160   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000503a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       35777   287378721   83  Linux
/dev/sdb4           35778       60801   201005280    5  Extended
/dev/sdb5           59842       60801     7711168+  82  Linux swap / Solaris
/dev/sdb6           35778       37257    11888037   82  Linux swap / Solaris
/dev/sdb7           37258       59841   181405948+  83  Linux

Partition table entries are not in disk order

```

I say occasionally since about once in every 3 boots, the partitions are mounted ok...  :confused:

Thanks for any help you can offer.

---

### Post by gweinstein on 2010-05-18
bump

---

### Post by gweinstein on 2010-10-08
OK, solved it.  Not such a big mystery, but hey, still some achievement for a non-expert like myself.

Turns out that somehow the OS would assign different device letters to the partitions on the two disks, sometimes naming one sda and the other sdb, and sometimes vice-versa.  Since the fstab was referring to the partition to mount by device name, this would occasionally fail.

The solution: edit fstab and refer to the partitions by UUID.  I had once read that this is more robust, but I guess I didn't pay enough attention.

I still don't understand why the device name changes from boot to boot.  I suppose it has to do with which one comes online first, but still, why would this change each boot?

Anyway, this seems to have solved the problem for now...

---

