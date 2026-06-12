---
title: "Install Windows to a linux software RAID?"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by Nachtengel on 2007-01-29
I have an AMD Athlon 4400+ X2 processor with a 939 socket.  After learning I could not run windows on Xen with this socket type/processor (needs an AM2 socket X2 for this to work) I have decided I'd like to take my Ubuntu only install & dual boot windows.  However, I have the SATA hard drives that have my /boot and / partitions on a linux software RAID.  I was curious if it were possible to install windows (XP) onto the extra space on these hard drives.  Also, I am having trouble getting gparted to recognize my software RAID... but I do have one.  Gparted only shows sda, sdb, sdc and sdd... where if I type 
```
user@host:$ cat /proc/mdstat
Personalities : [raid1] 
md2 : active raid1 sdb3[1]
      73151872 blocks [2/1] [_U]
      
md1 : active raid1 sdb2[1]
      4498112 blocks [2/1] [_U]
      
md0 : active raid1 sdb1[1]
      497856 blocks [2/1] [_U]
      
unused devices: <none>

```
so clearly I have a RAID up and working.  sda and sdb are two 80 gig drives which hold both /boot and /.  The other two drives are hooked up via LVM for my /home partition.  I would like to resize the / partition as it only takes a few gigs out of the 80 and allocate some space for dual booting windows.  Any help would be appreciated, as I have not been able to find any advice on this kind of a setup (windows installed to a linux software RAID).

---

### Post by Ivan_Avery_Frey on 2008-02-01
Windows cannot be installed onto a linux software RAID.

Ivan.

---

