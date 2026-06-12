---
title: "Dual boot and file systems"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by bigbadsi on 2007-02-15
I dual boot Ubuntu and Windows XP Pro (I only use XP for games!) on a single hard drive.  I'm running out of space on the Ubuntu partition so I've bought a new 320GB HD to both reinstall Ubuntu and to backup files on a remote Windows XP Pro HTPC.  My old HD looks like this:

[LIST]
[*]NTFS	96GB	XP
[*]ext3	8GB	Ubuntu root
[*]swap	2GB	Ubuntu swap
[*]FAT32	5GB	OS shared space
[/LIST]
I would like to install Ubuntu on the new HD, with the following considerations:
[LIST]
[*]lots of space for Ubuntu
[*]I would like to free up the 15GB non-NTFS partitions on the old HD for Solaris 10 (or whatever takes my fancy)
[*]lots of space for my HTPC backup files on the new HD
[*]I would like to be able to read and write to the backup partition on the new HD, from/to both (all) OSs.
[*]the Windows HTPC hardware is old, so if possible I would like to avoid running extra file system drivers on this machine
[*]disk performance
[/LIST]
I suppose I'm asking for a sensible file system to use for the HTPC backup partition on the new HD but also how much disk space is too much disk space for a Ubuntu installation?  I'm also unsure if it's wise to create a separate partition for /home, and if so how much space should be left for /root?  I don't create a lot of content in Ubuntu but I would certainly like to install a lot more.

Any advice or thoughts would be appreciated.

---

### Post by logos34 on 2007-02-15
> **bigbadsi said:**
> I dual boot Ubuntu and Windows XP Pro (I only use XP for games!) on a single hard drive.  I'm running out of space on the Ubuntu partition so I've bought a new 320GB HD to both reinstall Ubuntu and to backup files on a remote Windows XP Pro HTPC.  My old HD looks like this:

[LIST]
[*]NTFS	96GB	XP
[*]ext3	8GB	Ubuntu root
[*]swap	2GB	Ubuntu swap
[*]FAT32	5GB	OS shared space
[/LIST]
I would like to install Ubuntu on the new HD, with the following considerations:
[LIST]
[*]lots of space for Ubuntu
[*]I would like to free up the 15GB non-NTFS partitions on the old HD for Solaris 10 (or whatever takes my fancy)
[*]lots of space for my HTPC backup files on the new HD
[*]I would like to be able to read and write to the backup partition on the new HD, from/to both (all) OSs.
[*]the Windows HTPC hardware is old, so if possible I would like to avoid running extra file system drivers on this machine
[*]disk performance
[/LIST]
I suppose I'm asking for a sensible file system to use for the HTPC backup partition on the new HD but also how much disk space is too much disk space for a Ubuntu installation?  I'm also unsure if it's wise to create a separate partition for /home, and if so how much space should be left for /root?  I don't create a lot of content in Ubuntu but I would certainly like to install a lot more.

Any advice or thoughts would be appreciated.

You can install on as little as 2.5 gb, 10gb for root partition should be adequate for a typical setup, anything over 15gb is probably a waste of space.  

I would get fs-driver for windows (r+write ext2/3) and ntfs-3g for linux (r+w to ntfs).  A separate /home is nice because it makes linux reinstalls/upgrades a whole lot easier.

Check out the section on dual-boot partitioning over at psychocats.net.

---

### Post by bigbadsi on 2007-02-17
Thanks for you comments logos34.  I looked into fs-driver and it seems like the business.  ntfs-3g appears to have some problems but it's occurred to me that it's probably not that necessary for me anyway.

I decided to stick to ext3 and now my new 320GB disk looks like this:
[LIST]
[*]40GB  - root 
[*]256GB - home
[*]2GB  - swap
[/LIST]
I know that you explained that over 15GB for root was probably a waste of space but I suddenly felt disk-space rich and wanted to spend some of that currency.

Ubuntu is now reinstalled and configured.  This is just too easy.  Ubuntu rocks.

Again, thanks for your time.

---

### Post by logos34 on 2007-02-17
Ok. Enjoy!

---

