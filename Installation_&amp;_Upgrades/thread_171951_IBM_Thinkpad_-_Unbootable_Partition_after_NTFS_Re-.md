---
title: "IBM Thinkpad - Unbootable Partition after NTFS Re-Partitioning"
date: 2006-05-07
forum: Installation &amp; Upgrades
---

### Post by bennybobw on 2006-05-07
I posted [this thread]("http://www.ubuntuforums.org/showthread.php?t=171075") about an error that I got the first time installing Ubuntu.
The Windows error is this:
UNBOOTABLE_BOOT_PARTITION
Then it gives a hexadecimal address.

I reinstalled windows and tried simply reformatting the drive using the linus sysrescue cd.  I noticed before repartioning that there was 3.3 GB of "free space"  Is windows somehow using this space or could it simply not use this space when it converted the drive from fat32 to ntfs after installing XP?

Why do I keep getting the same error after repartitioning?  Note that this time I did it without touching the MBR.  Do I need to repartition using a Windows tool?  I've installed dual-boot systems before without this problem.  Also, I don't have a floppy drive so booting from a floppy is not an option.

---

### Post by Sef on 2006-05-08
Look at this to help you out:

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

---

### Post by bennybobw on 2006-05-11
Okay I after several failed attempts, I finally got it working by partitioning the hard drive using partition magic and then going through the normal install.  Thanks for your help!

---

### Post by Sef on 2006-05-11
You're welcome.  Be careful using partition magic.  Often it and Gnu/Linux don't get along, and that causes partition problems.

---

