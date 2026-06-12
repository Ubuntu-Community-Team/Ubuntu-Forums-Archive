---
title: "SAMBA preferred file system"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by ozz_man on 2011-07-08
Installing Ubuntu on fresh hard drives, need a SAMBA share on the second drive.  Is there a file system that I should use (ext4, ext3, NTFS, etc.)?

I will be accessing the share with:
- Ubuntu 10.04 (I have one older one but that'll be upgraded to this version)
- Windows XP, Vista, and 7

The entire second drive will be a big share, so the I'll be formatting the entire drive.  Can't seem to find any information on supported or recommended file systems.

Thanks in advance! :)

---

### Post by doas777 on 2011-07-08
I would recommend ext4 for performance and maintenances sake. NTFS partitions used by ubuntu don't get the same level of preventative maintenance that ext filesystems do, nor the level they would get in windows.

I try my very best to only use ntfs sparingly in linux. abrupt stops from powerfails really add up after a while.

Samba hides the filesystem type from the remote pc, so from the clients perspective, it doesn't matter what the underlying filesystem is.

---

### Post by ozz_man on 2011-07-08
That's sort of what I thought... wanted some confirmation... THANKS!

---

### Post by Morbius1 on 2011-07-08
It really doesn't matter. 

Samba hides the actual format of the partition the share is on from the remote user. The only real complication with an ntfs drive is if it's external and is mounted when plugged in since it's only accessible to the user that plugged it in. But even in this case Samba has a way around it.

---

