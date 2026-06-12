---
title: "Can't Install - HELP"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by Lemond on 2007-05-28
Hello All,

I am brand new to Linux.  I have taken an old PC (Celeron, 1.1ghz, 128mb RAM) and put a new Hitachi 320gb hard drive in it with the plans of making a backup server.  I downloaded the ISO of 6.1 and put it on a CD.  When I try to boot from this CD it runs through a series of checks and then stops at the DOS prompt a:\  I notice that it checks for FAT32 and NTFS and says "not found".  When I type d: it allows me to switch to the D drive (CD-ROM), but then I type c: it gives and error.  If I go to setup the new hard drive is there and seems fine- it gives the brand and size of the drive.  It does say "LBA Format" as opposed to FAT32 or NTFS.  Anyone have any ideas?  Bear in mind I've never used any Linux before - this will be my first!

Thanks,
Alan

---

### Post by Jussi Kukkonen on 2007-05-28
Lemond, this doesn't sound right... Linux does not refer to disks or partitions with drive letters, so "a:\" doesn't make any sense. In other words, if you had a "a:\"-prompt, it wasn't linux...

Some observations: You cannot install desktop ubuntu with 128MB of memory as far as I know. Installing the server version should be possible. However, I do not believe that booting the liveCD is even remotely possible with 128 MB.

---

