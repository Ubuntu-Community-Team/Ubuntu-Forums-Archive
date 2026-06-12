---
title: "screwed up partitioning"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by alican timur on 2007-08-12
I was installing ubuntu dapper drake from the live cd, and in the managing partition table manually tab during install, i resized the windows partition and created a linux filesystem in the free space, then proceeded. It applied some stuff, and after a short while it was in the partition formatting screen, and there were no ntfs partition or no ext partition, only the whole hard disk recognised as unformatted. 

i still got some really valuable stuff on the ntfs partition, and i was planning to resize & move stuff from partition to partition piece by piece.

---

### Post by alican timur on 2007-08-12
i'm on the live cd, so i've tried coding in:

> ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/hda1 /mnt/ubuntu

it didn't work. 
> 
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

fdisk -l command returns:

> 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14595   117234306   83  Linux
/dev/hda2           14596       14596        8032+  83  Linux


---

### Post by merlinus on 2007-08-12
From what I see, there are only linux partitions on your hdd.  But what is hda2, which looks as though it has almost no space?

You can try a system rescue cd to try and salvage data:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Or try to boot from a knoppix live cd.

-merlin

---

### Post by alican timur on 2007-08-12
i don't know what that little space is. Windoze xp leaves a little space like that whenever i create a partition during install..

---

### Post by merlinus on 2007-08-12
It also seems as though there is no /swap partition.

-merlin

---

### Post by alican timur on 2007-08-12
that big thing is not linux. I'm sure that it is not. it's supposed to be a primary partition with two secondary partitions. those should be like a ext partition and an ntfs partition.

---

### Post by alican timur on 2007-08-12
would a swap partition help anything right now?

---

### Post by merlinus on 2007-08-12
No.  Do not do anything until you have tried either (or both) of the two live cds to attempt recovering data.

-merlin

---

### Post by alican timur on 2007-08-12
ok. i'm downloading the rescue cd right now. by the way, there is something else.
something like this happened to me before, and i posted it here, and got solved. i tried to follow the same steps but it gave me the errors i posted here in the second post. the link to that thread is [this.]("http://ubuntuforums.org/showthread.php?t=369711")

---

### Post by merlinus on 2007-08-12
Yeah, but at that point your linux partition was hda6 (or sda6), and windows still existed.  Now linux is hda1, and no sign of windows.

-merlin

---

### Post by alican timur on 2007-08-12
okay i booted the cd up, there's a console now and i don't have any idea what to do.

---

### Post by merlinus on 2007-08-12
Which cd?  Was there not a Help option upon startup?

-merlin

---

### Post by alican timur on 2007-08-12
okay got it. every recovery sees it as linux.. i'm just formatting and installing ubuntu..

---

