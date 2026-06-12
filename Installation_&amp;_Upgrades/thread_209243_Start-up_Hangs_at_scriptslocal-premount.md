---
title: "Start-up Hangs at /scripts/local-premount"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by lukeblack on 2006-07-04
Hello.

When I start up my Ubuntu installation, it hangs with at the end of the following message (in recovery mode):

```
Begin: Running /scripts/local-premount...
[          28.96....] Attempting manual resume
[          28.96....] attempt to access beyond end of device
[          28.96....] sda2: rw=16, want=8, limit=2
[          28.96....] Kernel panic - not syncing: I/O error reading memory image
[          28.96....]  _
```

Here is some relevant information I obtained using a LiveCD.

```
root@ubuntu:/media/sda3# fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   83  Linux
/dev/sda2            5575        6148     4610655    f  W95 Ext'd (LBA)
/dev/sda3              69        5574    44226945   83  Linux (Ubuntu 6.06)
/dev/sda4   *        6149       24321   145974622+   7  HPFS/NTFS (Windows XP)
/dev/sda5            5575        5638      514048+  82  Linux swap / Solaris
/dev/sda6            5639        6148     4096543+  83  Linux (CentOS 4.3)

Partition table entries are not in disk order
```

```
root@ubuntu:/media/sda3# cat ./etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>          <options>                              <dump>  <pass>
/dev/sda3       /               ext3            defaults                                0       1
/dev/sda4       /media/sda4     ntfs            ro,auto,user,fmask=0111,dmask=0000      0       2
/dev/sda5       none            swap            sw                                      0       0
/dev/sda6       /media/sda6     ext3            defaults                                0       3
/dev/hdc        /media/cdrom0   udf,iso9660     user,noauto                             0       0
/dev/fd0        /media/floppy0  auto            rw,user,noauto                          0       0
proc            /proc           proc            defaults                                0       0
```

This problem occured after re-partitioning my hard-drive and installing CentOS 4.3. I would really appreciate any help.

Thanks in advance,
Luke

---

### Post by scxtt on 2006-07-04
off the top of my head, it looks like only your NTFS partition (/dev/sda4) is bootable ... but looking @ my "fdisk -l" none of mine appear bootable - hmm ...

maybe it's a problem w/ /dev/sda2?
[indent][          28.96....] attempt to access beyond end of device
[          28.96....] sda2: rw=16, want=8, limit=2

-----

/dev/sda2            5575        6148     4610655    f  W95 Ext'd (LBA)[/indent]

---

