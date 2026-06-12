---
title: "Make a new (RAID) partition available to all users"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by NogNeetMachinaal on 2009-12-27
I have installed 9.10 Desktop on a PATA disk.
I also have created a software RAID 0 partition based on 2 SATA disks.
That partition should mount on boot. And made available for all users.

The command 'cat /proc/mdstat' shows:
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid0 sdb1[0] sda1[1]
      312576512 blocks super 1.2 64k chunks
      
unused devices: <none>

The disk utility shows:
- a software raid GUID partition table.
- a raid volume md0
- a basic data partition called md0p1
- a mounteble filesystem labled 'Data'

If logged on as root, I can mount the filesystem. After that, I can read and write to this filesystem.
However, when logged on as a regular user, I can not.

How can I make sure that this filesystem will mount at boot time?
What do I need to change for making this partition available to all regular users of that system?
I have spend several hours reading all kind of how-to's and wiki's.
But sofar no such luck.

---

