---
title: "'No root file system' - but there is"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by DocFox on 2007-02-19
Hi

I'm hoping that i'm not missing anything obvious. I have two SATA disks set up thus:
[indent]
ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       10010    59922450    f  W95 Ext'd (LBA)
/dev/sda5            2551        5100    20482843+   b  W95 FAT32
/dev/sda6            5101        5229     1036161   82  Linux swap / Solaris
/dev/sda7            5230        7841    20980858+  83  Linux
/dev/sda8            7842       10009    17414428+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    c  W95 FAT32 (LBA)
[/indent]

This a hangover from installing XP (OS on sda1 and sda5) and SUSE on sda6-8.

My current plan is to install ubuntu 6.1 to sda6,7,8 (swap, / and /home, respectively). The new disk is sdb, which i want to use to store video files.at /media/movies and for the sake of Mrs F, mount sda5 at /media/windows. i added /media/XP for sda1 for completeness, although i think i'll disable it as an automounted partition.

So I get to this screen and it tells me that I haven't defined a root file system, when i have,,,

[IMG]file:///home/ubuntu/Screenshot-3.png[/IMG]


I find this rather puzzling. Can anyone point me in the right direction?

---

### Post by DocFox on 2007-02-19
Sorry the graphic didnt load, but in screen 5 of 6 of the install wizard, it asks where to mount each partition. i will recreate the relevant bits here.
[INDENT]
mountpoint       partition
/                        sda7
/home                sda8
/media/windows  sda5
swap                  sda8
/media/movies    sdb1
/media/XP           sda1[/INDENT]

i'm truely bamboozled by the message 'No root file system'

---

### Post by confused57 on 2007-02-19
I believe it's a problem many people have had with the live cd, I think the workaround was to pre-format the partition(s) before trying to install...you can use the gparted live cd(approx. 30 mb download):
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Topsiho on 2007-02-19
I have to use the -p option to see the partition table with fdisk :)
You then get the partition table with all the pertinent information but not the mountpoints.

To see the mountpoints you could read the /etc/fstab file with

less /etc/fstab

Topsiho

---

### Post by DocFox on 2007-02-19
well i tried a minor scale re-partition with gparted and no change
infact the install wizrd cals gparted to do the partitioning so i'm not surprised that there was no change.
still no further along

---

### Post by rsambuca on 2007-02-19
It's a known bug with the ubiquity installer.  You can find a workaround here.

[[COLOR="Red"]Link[/COLOR]]("http://www.ubuntuforums.org/showpost.php?p=1700787&postcount=29")

---

### Post by DocFox on 2007-02-19
rsambuca you are a gentleman (or gentle-lady of course, who can say in a forum)

U6.10 install chugging away on the other machine. was ready to smash the damn thing with a hammer until i read your post.

as a side issue - if this is a known bug with a *very* easy fix, why havent the downloadable iso files been updated? does anyone know? seems like a particularly glaring flaw in the distribution of the software.

thanks again

---

### Post by DocFox on 2007-02-19
yes, that's one copy of U6.1 up and running smoothly in 20 minutes (and 6 hours faffing around)

---

