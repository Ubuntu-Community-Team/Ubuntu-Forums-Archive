---
title: "About unreadahead and /var"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by LarsUb on 2011-09-26
Hi guys, this is my question:

**Which version (lucid 10.04.3 or 10.10 maverick) is best to install a 64bit system with a /var partition separated from / , and at the same time having the 'benefits' of the unreadahead.conf ??.**

I feel dissapointed since i have to reinstall my whole (most apps compilated) system due to a crashed booting derivated from the eliminated /var directory after running fsck in my current Lucid 10.04.2 amd64bit installation. My workaround is posted here: [http://ubuntuforums.org/showthread.php?t=1850309]("http://ubuntuforums.org/showthread.php?t=1850309")

I haven't found a solution, i've lost one job day and another will be lost, because (googling this issue) it seems theres is no option other than to reinstall my whole system again but now with a separate /var partition, to avoid problems with corrupted inodes, fsck and the famous unreadahead.conf. 
All related to answers 11-14 according to this bug [https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/523484]("https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/523484")

So, which is best?, I want to reinstall with a separetad partition for /var, in order to avoid the GIANT PROBLEM of lost /var under /, but at the same time keep the 'performance benefit' of the ureadahead,
I need to reinstall ASAP.

---

