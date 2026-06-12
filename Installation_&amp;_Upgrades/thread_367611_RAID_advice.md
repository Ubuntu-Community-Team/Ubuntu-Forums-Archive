---
title: "RAID advice"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by tog_benson on 2007-02-22
I am setting up a web server.  I am going to employ RAID 1 using two 40 GB drives and I want to make intelligent decisions regarding the layout.

**Does anyone have an opinion on using raid partitions for swap?**   I've read some stuff that says it isn't necessary/useful, but I have also read that it is good to have swap on raid for obvious reasons (drive dies, swap still works and system doesn't fail)

**How about putting /boot in RAID?**  I've seen some documentation describing keeping /boot out of RAID in case raid craps on itself.  Some people seem to suggest having a /boot on one drive (partition 1) and keep it sync'ed with the first partition on the second drive.  Then if drive 1 fails, configure the second drive as /boot.

Any ideas welcome.

---

### Post by sheepshearer on 2007-02-22
here's what i did recently:

[http://ubuntuforums.org/showthread.php?t=366315]("http://ubuntuforums.org/showthread.php?t=366315")

i partitioned:
```

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          16      128488+  fd  Linux raid autodetect
/dev/hda2              17        3663    29294527+  fd  Linux raid autodetect
/dev/hda3            3664       14471    86815260   fd  Linux raid autodetect
/dev/hda4           14472       14593      979965   82  Linux swap / Solaris

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1          16      128488+  fd  Linux raid autodetect
/dev/hdc2              17        3663    29294527+  fd  Linux raid autodetect
/dev/hdc3            3664       14471    86815260   fd  Linux raid autodetect
/dev/hdc4           14472       14593      979965   82  Linux swap / Solaris
```

i RAIDed partitions 1,2,3:

```
# cat /proc/mdstat 
Personalities : [raid1] 
md2 : active raid1 hda3[0] hdc3[1]
      86815168 blocks [2/2] [UU]
      
md1 : active raid1 hda2[0] hdc2[1]
      29294400 blocks [2/2] [UU]
      
md0 : active raid1 hda1[0] hdc1[1]
      128384 blocks [2/2] [UU]
      
unused devices: <none>

```

and i kept 2 **independent** swaps for speed:

```
# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

#/dev/md1=/dev/hda2,hdc2
UUID=4ecba4c2-543c-43a8-a1a2-bbeaa806ae9e / ext3 defaults,errors=remount-ro 0 1
#/dev/md2=/dev/hda3,hdc3
UUID=592c72f9-0554-4788-821d-3fb6d8c2106c /home ext3 defaults 0 2
#/dev/md0=/dev/hda1,hdc1
UUID=656c3be1-010c-43b7-b5fa-dc8ad18d67b9 /boot ext3
# /dev/hda4
UUID=43e61fc0-ad49-4a1e-9f28-fdd0228b3093 none swap sw 0 0
# /dev/hdc4
UUID=fdbcf78e-7e45-4222-a68f-243ceb47724a none swap sw 0 0 

```

---

### Post by tog_benson on 2007-02-22
Thanks for the input.

I keep flip-flopping with regards to the swap config.  I think I'll just keep normal swap on normal partitions, but I keep going back to "what if my drive fails and my swap disappears and crashes the server?"  It is speed vs. stability at this point.  It'd be nice for the swap to be raided and withstand a drive crash.

Either way thanks for your info.

---

### Post by sheepshearer on 2007-02-22
AFAIK RAID 1 will degrade disk write performance - may not be what you want on a swap disk.

i guess your system could crash if the swap drive died and it wasn't mirrored, but at least it would come back up OK on the good drive.

i'm no RAID expert at all - my first play with it was prompted by

[LIST=1]
[*]ignorance :)
[*]this article on [linuxjournal.com]("http://www.linuxjournal.com/article/5653")
[/LIST]

---

### Post by sheepshearer on 2007-02-23
i've been thinking about this and read [here]("http://lkml.org/lkml/2006/9/3/142") that the essential kernel structures shouldn't swap out. that leaves pretty much only user data in swap.

so i'm going to retro fit RAID to my swap. it''l reduce y swap space from 2x1Gb to just 1Gb, but i only have a 512Mb RAM system anyway and could easily add to that. that thread correct;y points out that if you're swapping,you're already running like a 3 legged dog so what's a bit of write performance loss going to do?

so i'm decided - i'll go for the max imum reliability RAID1 can offer me

thanks for making me think a bit further :)

---

