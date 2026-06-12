---
title: "How Do I Upgrade From One Computer to Another"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by rincewind1013 on 2006-11-18
I'm going to be moving my linux machine from an Celeron 2Ghz on an ECS VIA P4M800 PRO motherboard to a Core 2 Duo on an Intel G965 board. My question, how do I do that?

To further expand,
Current System: Ubuntu Edgy Eft 
Kernel: Linux tivo 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux
fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1 -- converted during upgrade to edgy
UUID=065448c7-0098-4bbe-a6c1-d207b4201a1a /boot ext3 defaults 0 2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/md0        /tivo           xfs     defaults        1       3
/dev/mapper/Ubuntu-extra        /extra  xfs     defaults        0       0

```
The system drive is on a SATA drive, sda. sda has a lvm volume group - Ubuntu which has my /, swap, and /extra
I have a 3 disk  PATA raid 5, md0
mdadm.conf:
```

DEVICE /dev/hdb1 /dev/hdc1 /dev/hdd1
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=b77234e1:6623a286:be784209:68ec40f6

```


What's the process like for changing systems? Do I just put the system drive in the new machine and hope it works? 
My real concern is the raid. The Intel motherboard only has one PATA channel, so I'll need to get a controller card. Will that mess up the raid? Should I just comment out the md0 from fstab so Ubuntu doesn't try to mount it, until I figure out what names the drives would get so I could modify mdadm.conf

Thanks for any help

---

