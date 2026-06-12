---
title: "help mounting FreeBSD drives in hardy"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by Batmanatthenewb on 2008-11-24
Running Hardy. Can mount a FreeBSD drive with the command:

mount -t ufs -r -o ufstype=ufs2 /dev/sdb1 /media/ufsdisk1

Can see and access all my files but do not have read/write ability. Also, can not figure out the correct command to put in fstab to permanently mount the drive. Any help would be appreciated. Thank you.

Also posted in Hardware and laptops area three days ago with no response.

---

### Post by Mr-Biscuit on 2009-03-14
UFS2 r/rw support is experimental at best.

Howto at debian forums to cover such.
[http://forums.debian.net/viewtopic.php?t=27227](http://forums.debian.net/viewtopic.php?t=27227)

You'll have to disable security to read the /home/ directories. I don't suggest doing such.

---

