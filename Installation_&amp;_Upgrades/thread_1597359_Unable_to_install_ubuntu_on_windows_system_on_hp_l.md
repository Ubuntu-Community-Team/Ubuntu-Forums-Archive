---
title: "Unable to install ubuntu on windows system on hp laptop"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by kask1984 on 2010-10-15
hi,
my problem is extension of following threads


[http://ubuntuforums.org/showthread.php?t=1403747](http://ubuntuforums.org/showthread.php?t=1403747)
[http://ubuntuforums.org/showthread.php?t=1403414](http://ubuntuforums.org/showthread.php?t=1403414)

i am trying to install ubuntu10.04 on windows7 in HP laptop.
i followed above threads and deleted HP_TOOLS and HP recovery.

i am trying to install ubuntu using USB flash drive.

when i am at the step of partitioning the HDD it is not able to show the freespace (unalloted space)
it is just showing two drives with sizes (aprox)----150GB  and 160 GB (my total HDD size is 320 GB).

I attached windows7 Disk management window.

I want to install ubuntu on 60GB free space.
Actually i tried Gparted in ubutnu, it said it will remove all the from hard disk (it is treating whole HDD as single drive).
How to install ubuntu on that freespace.

thanks

---

### Post by efflandt on 2010-10-15
Notice that Windows says the partitions are "Dynamic" NTFS.  That is NOT simple msdos partitioning that just any partitioning program can do.  It is a Windows specific logical dynamic volume partitioning that other tools may not be able to cope with yet, because it can change on the fly.

I don't know how easy that is to change.  Fortunately the Dell I recently bought with Win7 does not do that, maybe because Dell is Linux aware (and has even sold systems with Ubuntu instead of Windows).

In the meantime, if you can afford it, you might want to pick up a portable USB hard drive and install Ubuntu there.  But make sure that you put grub on the mbr of the USB drive.  You could boot from there by changing BIOS boot order, which sometimes still requires pressing a specific key during BIOS splash screen to boot from something other than the internal hard drive.  I do that for an older work laptop that I do not want to tamper with.

I hope you used the HP utility to create your utility and system recovery discs already, because it is probably too late to do that if you already removed the HP Recovery partition.

---

