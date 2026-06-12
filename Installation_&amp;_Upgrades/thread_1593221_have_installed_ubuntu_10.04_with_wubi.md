---
title: "have installed ubuntu 10.04 with wubi"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by alexchrist on 2010-10-11
i have installed ubuntu 10.04 with wubi installer and now i want to uninstall windows xp what shall i do???:confused:

---

### Post by bcbc on 2010-10-11
> **alexchrist said:**
> i have installed ubuntu 10.04 with wubi installer and now i want to uninstall windows xp what shall i do???:confused:

Your wubi install is on a virtual disk that is actually a file within the windows ntfs file system.

You could either: 
Back up your data, get a list of installed programs from Ubuntu and then do a fresh install over the whole drive.
Or
You can create a new partition for Ubuntu and [migrate your wubi install]("http://ubuntuforums.org/showthread.php?t=1519354") to it - then once it's successfully booting just reuse your ntfs partition containing Windows.

---

### Post by alexchrist on 2010-10-13
> **bcbc said:**
> Your wubi install is on a virtual disk that is actually a file within the windows ntfs file system.

You could either: 
Back up your data, get a list of installed programs from Ubuntu and then do a fresh install over the whole drive.
Or
You can create a new partition for Ubuntu and [migrate your wubi install]("http://ubuntuforums.org/showthread.php?t=1519354") to it - then once it's successfully booting just reuse your ntfs partition containing Windows.

how do i create a new partition:confused::confused::confused:

---

### Post by bcbc on 2010-10-13
[How to resize windows partitions.]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions")

PS for XP you should run the disk defrag at least twice.

Also [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Here's a more detailed description of partitions: [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
It looks complicated... but read through it. There are links to other guides as well. Make sure you also figure out how to backup your current setup. Partitioning carries some risks and it pays to have a backup if something goes wrong.

---

