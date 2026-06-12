---
title: "LVM can't handle my volumegroup after upgrade to 11.04"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by zteifel on 2011-05-09
Hi!

I have a volumegroup created with linux volume manager LVM. It consists of 3 physical disks, 1 volumegroup (vg1) and 1 logical volume (lg1). 

```

ubuntu@ubuntu:~$ sudo pvscan
  PV /dev/sde   VG vg1   lvm2 [931,51 GiB / 0    free]
  PV /dev/sda   VG vg1   lvm2 [279,48 GiB / 0    free]
  PV /dev/sdb   VG vg1   lvm2 [279,48 GiB / 44,00 MiB free]
  Total: 3 [1,46 TiB] / in use: 3 [1,46 TiB] / in no VG: 0 [0   ]

ubuntu@ubuntu:~$ sudo lvscan
  ACTIVE            '/dev/vg1/lg1' [1,46 TiB] inherit

ubuntu@ubuntu:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "vg1" using metadata type lvm2
ubuntu@ubuntu:~$ 

```

Everything works great with ubuntu 9.10. But when upgrading, or starting with live 11.04 the problem begins.


I get this when i try to activate my volumegroup
```

ubuntu@ubuntu:~$ sudo vgchange -ay
  device-mapper: resume ioctl failed: Invalid argument
  Unable to resume vg1-lg1 (252:0)
  1 logical volume(s) in volume group "vg1" now active

```

If i check the log, i see this:
```

May  9 14:45:15 ubuntu kernel: [  200.776060] device-mapper: table: 252:0: sda too small for target: start=384, len=586113024, dev_size=586112591

```
In 9.10 i have both /dev/mapper/vg1-lg1 and /dev/vg1/lg1 but in 11.04 i only have /dev/mapper/vg1-lg1

I have restored the volumegroup with vgcfgrestore and that works but doesn't help.

I read something a while ago about meta-data traces of previous raidconfiguration that could lead to problems with new versions of lvm. Therefore i did dmraid -ay and discovered some traces on both sda and sdb.
I erased it with dmraid -rE and nothing shows up when i do dmraid -ay anymore. Still the problem isn't solved.
(edit: I actually find a bugreport where it said this could be the problem: [https://bugzilla.redhat.com/show_bug.cgi?id=505291]("https://bugzilla.redhat.com/show_bug.cgi?id=505291"))

I also tried to resize the logical volume because the messages in the log, but that didn't help either. I'm out of ideas and google as hell all weekend. Im guessing this is probably an easy fix, but I'm stuck!  

Please help!

---

### Post by zteifel on 2011-05-09
Some additional info:

I discovered something i should have seen before. The log says basically its sdc that is to small.

```
May  9 15:40:12 ubuntu kernel: [  213.383979] device-mapper: table: 252:0: sdc too small for target: start=384, len=586113024, dev_size=586112591
```

fdisk -l shows that this might be the case, Even though the disk should be identical to sdd, sdc  is approximately ~1MB smaller then sdd. 

Could it be that this newer version of ubuntu identify som bad sectors or something on sdc, and thus the logical volume is bigger than the physical volume? The resize i did only affected sdd as you can see in the previous post. Is there anyway to decide which pv the resize of lv should affect? 

```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sdc 

Disk /dev/sdc: 300.1 GB, 300089646592 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sdd

Disk /dev/sdd: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

```

Edit: I booted with a 9.10 live cd and fdisk -l show that the disc are of equal sizes:
```
zteifel@zteifel-server:~$ sudo fdisk -l
[sudo] password for zteifel: 

Disk /dev/sda: 300,1 GB, 300090728448 byte
255 huvuden, 63 sektorer/spår, 36483 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x00000000

Disk /dev/sda innehåller inte en giltig partitionstabell

Disk /dev/sdb: 300,1 GB, 300090728448 byte
255 huvuden, 63 sektorer/spår, 36483 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x00000000

```

---

### Post by zteifel on 2011-05-10
I have an idea of how to solve this. I need to reduce the lvsize of lg1 on /dev/sda with 1 extent.

But i cant do this because it says that the specified PV doesn't have space avaible, which is true, acording to pvdisplay.

```
zteifel@zteifel-server:~$ sudo lvreduce -l-1 vg1/lg1 /dev/sda
[sudo] password for zteifel: 
  No free extents on physical volume "/dev/sda"
  No specified PVs have space available
zteifel@zteifel-server:~$ 

```
```
zteifel@zteifel-server:~$ sudo pvdisplay /dev/sda
  --- Physical volume ---
  PV Name               /dev/sda
  VG Name               vg1
  PV Size               279,48 GB / not usable 840,00 KB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              71547
  Free PE               0
  Allocated PE          71547
  PV UUID               HnovSp-akYP-K63j-28PY-ITaR-8cmm-5od8pR

```

I have added a new phsycical volume to the volumegroup and extended the logigal volume. What i need to do is move at least one extent to the new physical volume. To do this, there is the pvmove command, but i only figured out how to do this with the hole disk. I need something to specify which exent to move like pvmove -l 71547 /dev/sda /dev/sdc. But that isnt possible.

The closest thing i got is 
[-n/--name  LogicalVolume] [SourcePhysicalVolume[:PE[-PE]...] [DestinationPhysicalVolume[:PE[-PE]...]...]
Which should be something like pvmove -n /dev/vg1/lg1 /dev/sda/:71547 /dev/sdc:71547 
but this only give me:
```
zteifel@zteifel-server:~$ sudo pvmove -n /dev/vg1/lg1 /dev/sda:71547 /dev/sdc:71547
  PE range error: start extent 71547 to end extent 71547

```

The other possibility  i figured out is to let the disk defrag itself by regular activity to the disk. Could this work?

Somehow i need to remove 1 logical extent from /dev/sda. Could this be accomplished with some type of mirroring?

A lot of questions and bad some english. I hope someone is willing to help... :-)

---

