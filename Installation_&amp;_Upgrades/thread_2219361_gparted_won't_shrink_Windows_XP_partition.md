---
title: "gparted won't shrink Windows XP partition"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by Bob_Shabowski on 2014-04-23
I am trying to dual boot lubuntu on an older computer (1024 mb RAM) and need to shrink the windows XP (ntfs) partition to make room for a lubuntu one. I have tried to use the partitioner built in with the boot cd, but it didn't work, so I did the 'try lubuntu' option and opened gparted. The disk has an exclamation point next to it, and when I go to 'Information' at the bottom I get this:
```
Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:  ntfsprogs / ntfs-3g.
```
I installed the second package again, but could not find the first in Synaptic. Anyway, my issue is that when I right click->resize/move, I cannot shrink it (but I can grow it w/ the 10 mb unallocated); the buttons go grey. I've done this sort of thing with linux mint on another computer before successfully, so I have no idea what might be wrong. I can mount and open the disk, and when mounted gparted shows the 10 gb free space that it has. Any help would be greatly appreciated.

---

### Post by oldfred on 2014-04-24
ntfsporgs merged with ntfs-3g, so it now is just one package. It should be installed by default.

But the NTFS driver will not mount NTFS partitions that are hibernated or need chkdsk. And NTFS needs chkdsk after any resize. So be sure to reboot Windows immediately after any partition size change before installing Ubuntu.

Best to run chkdsk and defrag Windows first. You cannot do that from Linux but either inside Windows if it works or using your original XP install disk or any other Windows repairCD or flash drive.

---

