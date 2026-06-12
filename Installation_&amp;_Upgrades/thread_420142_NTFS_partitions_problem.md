---
title: "NTFS partitions problem"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by GwydionThendon on 2007-04-23
Hi,
I recently installed Ubuntu 7.04 and everything gone right. However I discovered that the NTFS partition already present on my hd was mounted in read-only. So I installed the ntfsconfig tool to set the permission as read/write. Unfortunately when I started the tool the first time and I tried to change the permissions it returned an error saying that there was an error in the ntfs logfile. The result is that now the ntfs partition disappeared and I cannot access it anymore. Do you know a way to fix this?

Thanks

---

### Post by joft on 2007-04-23
I think, if there is something wrong with the log file, the safest way, to repair it, is booting into M$ Windows (and perhaps running chkdsk on it) and shuting down properly.

---

### Post by GwydionThendon on 2007-04-23
This is what the NTFS tools suggested me to do. However I haven't got Windows anymore, since I uninstalled it before installing Ubuntu. Do you think is a partition problem or maybe reinstalling Ubuntu it could be fixed?

---

### Post by joft on 2007-04-24
Hmm, you could use "ntfsfix" (in package "ntfsprogs"), but in fact that's not a solution either, because the man page of ntfsfix suggests to reboot into Windows, too.

Reformating the partition using a Linux filesystem (ext3, reiserfs, ...) seems to be the best solution. But I assume you are having files an that partition and you want to backup them before reformating. So you could use "ntfsmount" (also in package "ntfsprogs") with the options "force" and "ro" (see man page for details) to mount it and read/copy all files.

---

