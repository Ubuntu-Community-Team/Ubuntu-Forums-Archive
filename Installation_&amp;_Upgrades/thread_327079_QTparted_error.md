---
title: "QTparted error"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by tom1979 on 2006-12-28
Im unable to use QTparted, it gives error message "no device found.Maybe youre not using root user?"

im trying to disolve 2 partitions from a failed install attempt. my disc partitions look like this:
Partition 1 device: /dev/hda1 (17gb windows xp part)
Free Space not partitioned(4gb unavailabe, i think this has the failed ubuntu on it)
Partition 2 device /dev/hda1 (9.6gb this is the ubuntu main partition ext3)
swap partition 1.3gb self explanetry
Free Space not partitioned (148.15 mb unavailable, this was the failed instalation swap space)
Partition 5 device /dev/hda5 (8.8gb vfat file system for shared win/ubunto files) 

as you can see i installed on the wrong partition initially after using disk magic in windows,this partition got repartitioned by ubuntu. then i installed again with usable partition sizes, but im losing 4gb of space, which is quiet a lot on a 37Gb hdd! 

The grub boot screen recognises 2 ubuntus and a xp OS at start up, but im now unable the boot the screwed up ubunto. so how can i get the space back?!

im pretty new to ubuntu, but so far been able to intall,upgrade, and set wifi up with the help of this forum, so have high hopes somebody can help!
thanx in advance, Tom.

---

### Post by Bartender on 2006-12-28
If you've got access to broadband, just try [GParted ]("http://gparted.sourceforge.net/livecd.php")instead.

---

### Post by tom1979 on 2006-12-28
brilliant cd to make and use... however, i only freed up about 7mb! gparted  shows the 4 partitions i want to see now instead of 6.however back in ubuntu disks manager im finding :
partition 1 (17.33GiB)
free space (4096.00GiB)
partition 2 (9.64 GiB)
swap partition (1.47Gib)
partition 5 (8.82GiB)

37.26GiB is the size off the hdd in both ubunto disk manager ans gparted, so this free space doesnt exist!! wheres it come from?! also the figure is 4096.0 GiB! is this just a glich i shouldnt be bothered by?

---

