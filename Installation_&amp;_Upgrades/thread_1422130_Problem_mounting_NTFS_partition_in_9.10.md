---
title: "Problem mounting NTFS partition in 9.10"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by mapage on 2010-03-05
I am trying to mount 3 NTFS partitions, but they aren't showing up in the /dev directory.  If I fdisk the drive, the partition shows up, but nothing in /dev...  

Here is the output of fdisk -l as well as the results of my attempt to mount the partition.

(I know loggin in as root is a bad thing, but I got tired of typing sudo this and sudo that...  Don't hate me because I'm beautiful...)

root@MountainPeak:/dev# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000209b3

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00017094

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2ac9c27

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       33590   269805854    7  HPFS/NTFS
/dev/sdc2           33591       60801   218572357+   5  Extended
/dev/sdc5           33591       60315   214668531   83  Linux
/dev/sdc6           60316       60801     3903763+  82  Linux swap / Solaris

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d068

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30401   244196001    7  HPFS/NTFS
root@MountainPeak:/dev# mount /dev/sdd1 /mnt
mount: special device /dev/sdd1 does not exist

---

### Post by byStanderone on 2010-03-05
...go synaptic manager and findout it ntfsprogs is installed...if not, install it for your system to be able to do work on an ntfs partition.

---

### Post by mapage on 2010-03-06
I should have mentioned that I have another (/dev/sdc1) NTFS partition that is working correctly.  I've found other people online that have similar problems as I am, but it seems that people try to help and ask questions then the original poster never responds with what fixed it.

It's just strange that it works great for 1 of the 4 NTFS partitions I have on this computer.  Don't know if it matters, but they are all SATA drives and earlier (right after the install) the three NTFS drives in question seemed to be in a RAID array.  I don't know why 9.10 thought they were in an array.  Probably just a red herring.

Thanks for the reply.

---

### Post by byStanderone on 2010-03-06
...i see, will return to this thread in a little while, will just go back on something i read about preferred number of partitions that karmic is defaulted to handle...if i remember correctly, it is recommended that only two hdd should be used. anyway will verify it...

---

### Post by byStanderone on 2010-03-06
...this is what i got so far, don't know if you've seen this :

[http://ubuntuforums.org/showthread.php?t=537433](http://ubuntuforums.org/showthread.php?t=537433)

---

### Post by mapage on 2010-03-09
That link doesn't seem to apply...  It appears that the /dev/device existed for him, but it doesn't for me.  

Something of interest though... I emptied one of the drives from Windows and then repartitioned it in Linux.  The drive and letter appeared correctly in linux (still set it up as NTFS though).  Then I logged back into Windows so I could copy stuff to the drive.  The end goal is to reformat all of the NTFS drives as ext4 and move all of my files there.  I don't know why it isn't working, but I guess I can just punt and copy everything to an external drive, reformat the internal drives and then move the files off of the external.  I was hoping to avoid the external step because it's so slow.

Did I post this in the wrong place?  I was expecting more ideas.  Maybe this isn't a common enough problem.

Thank you for your help byStanderone.

---

### Post by byStanderone on 2010-03-13
...no problem, thank you as well, one thing about this forum...it works both ways.

---

