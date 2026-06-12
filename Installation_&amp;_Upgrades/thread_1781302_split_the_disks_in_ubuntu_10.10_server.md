---
title: "split the disks in ubuntu 10.10 server"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by laith1952 on 2011-06-13
**[FONT=Arial][SIZE=2][COLOR=blue]Dear Sirs,[/COLOR][/SIZE][/FONT]**

**[FONT=Arial][SIZE=2][COLOR=blue]We are looking for your kind help with many thanks ...[/COLOR][/SIZE][/FONT]**

**[FONT=Arial][SIZE=2]We installed ubuntu 10.10 server in dell T 710 server with two disks raid 1[/SIZE][/FONT]**
**[FONT=Arial][SIZE=2]We want split the disks :[/SIZE][/FONT]**
**[FONT=Arial][SIZE=2][COLOR=blue]Disk 0[/COLOR] for ubuntu 10.10 server with htdocs[/SIZE][/FONT]**
**[FONT=Arial][SIZE=2][COLOR=blue]Disk 1[/COLOR] for other htdocs and many other documents[/SIZE][/FONT]**

**[FONT=Arial][SIZE=2][COLOR=blue]please how we do that with many thanks ...[/COLOR][/SIZE][/FONT]**

---

### Post by aphatak on 2011-06-13
When you created a RAID-1 configuration, you set it up so that the two disks mirror each other: the same data is written to both the disks in parallel.  The idea is, if one hard disk fails, the other will probably continue working and you won't lose data.  This also means that you have a disk array with the capacity of only one drive (the smaller of the two if they are not equal in size) that is twice as reliable as a single drive.

I know of no way to split these disks back into two without re-formatting the lot and thus destroying the array in the process.

---

