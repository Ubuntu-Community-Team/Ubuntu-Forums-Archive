---
title: "RAID problem after reinstall"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by leikarnes.2 on 2010-04-12
Hi

After Ubuntu 9.10 reinstall Pailimpsest Disk Utility won't/cant start my 3-disk RAID5 of 3x2TB Hitachi disks(encrypted).

Directly after the reinstall disk utility didn't recognize my RAID att all.

[[img]http://bildr.no/thumb/626761.jpeg[/img]](http://bildr.no/view/626761)

But after I installed mdadm, updated and restarted, ubuntu now recognizes parts of my RAID 

[[img]http://bildr.no/thumb/626763.jpeg[/img]](http://bildr.no/view/626763)
 

Now if I press the "add" button and chose one of my 2TB disks I get the following error:

```
Error adding component: mdadm exited with exit code 1: mdadm: cannot get array info for /dev/md_d127
```


If I press the "Stop the array" button I get the options to also push the "Attach" and "Repair" buttons.
If I press the "Repair" button nothing happens, and if I press the "Attach" button I get the following error message:

```
Device is not a Linux md drive
```


[[img]http://bildr.no/thumb/626764.jpeg[/img]](http://bildr.no/view/626764)





Some extra information:



```
root@pc1:~$ uname -r
2.6.31-14-generic

```

```
root@IBM:~# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bf8dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204794880    7  HPFS/NTFS
/dev/sda2           25497      121601   771963412+   5  Extended
/dev/sda5           25497       31575    48829536   83  Linux
/dev/sda6           31576       34007    19535008+  82  Linux swap / Solaris
/dev/sda7           34008      121601   703598773+  83  Linux

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00075221

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005ffb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00085833

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001   fd  Linux raid autodetect

```

---

