---
title: "Can't see/resize ubuntu partition"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by sinusance on 2010-10-15
I am dual booting Windows 7 and Ubuntu on my laptop, and I'm trying to resize my ubuntu partition to make it larger.  When I boot from the GParted Live disc , however, It only recognizes the existence of my 160 Gig windows NTFS partition which has ~15 Gigs of free space, which I want to reformat and expand ubuntu into (I freed that space by shrinking my windows partition from inside windows 7).  I know my Ubuntu partitions are there (I'm in Ubuntu now, plus my HD is 200 Gigs not 160), but I can't see them.

I have a feeling this has something to do with my resizing of my windows partition from windows, but I'm not sure.

more info:
```

sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1950c5c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   279813807   139905880    7  HPFS/NTFS

```

This is my first post, so if I haven't given enough information, please let me know.

---

### Post by oldfred on 2010-10-15
Welcome to the forums.

Do you have a full install with partitions or a wubi install that is just a file inside your windows NTFS partition?

If when you boot you get the windows choice first then a second menu from grub with Ubuntu or windows you have wubi.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning.

---

### Post by Mark Phelps on 2010-10-15
If you can still get into Ubuntu, then you could only have installed it via Wubi -- which does NOT partition the drive at all; instead, it creates a large file INSIDE the NTFS partition that Ubuntu then treats as a partition.  You can't resize this using partitioning tools because it's not actually a partition.

---

### Post by sinusance on 2010-10-15
Thanks for the quick responses guys!
You are right, I am using Wubi.  I've re-formatted this drive and re-installed windows/ubuntu so many times I forgot how I had installed it this time.

---

### Post by oldfred on 2010-10-15
If it is really a 200GB drive then the 240 heads shown may be part of the issue as drives are all LBA and the default then is 255 heads. 

Windows/NTFS needs 20-30% free space to keep working well, so you do not have a lot of room.

---

