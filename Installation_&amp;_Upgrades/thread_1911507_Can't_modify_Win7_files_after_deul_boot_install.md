---
title: "Can't modify Win7 files after deul boot install"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by rough60 on 2012-01-19
Hi all,

After setting up ubuntu server I decided to make my Win7 laptop duel boot.
Laptop is HP dv7 with 2 500Gb hard drives, one drive has windows, recovery, ubuntu, and swap partitions. The 2nd disk has all my files on it and is NTFS.

All works perfect except when I'm in ubuntu and trying to edit files on the 2nd disk I originally created in windows, it tells me I can only modify a copy of the file because there may be missing access rights.

I booted windows and allowed sharing on the whole drive but this did nothing for the problem.

What do I need to do?

Cheers.

---

### Post by Mark Phelps on 2012-01-19
Are you Hibernating Win7 while you are attempting to access the shared drive in Ubuntu? If so, that will give you major problems.

If not that, then check to see if ntfs-3g is installed in Ubuntu.  It used to be installed automatically, but now, it conflicts with ntfsprogs and is no longer installed.  If it is not installed, then install it -- you will get prompted to remove ntfsprogs.  Allow it to do that.

After ntfs-3g is install, reboot.  You should then be able to access your shared NTFS partition without problems.

---

### Post by rough60 on 2012-01-23
> **Mark Phelps said:**
> Are you Hibernating Win7 while you are attempting to access the shared drive in Ubuntu? If so, that will give you major problems.

If not that, then check to see if ntfs-3g is installed in Ubuntu.  It used to be installed automatically, but now, it conflicts with ntfsprogs and is no longer installed.  If it is not installed, then install it -- you will get prompted to remove ntfsprogs.  Allow it to do that.

After ntfs-3g is install, reboot.  You should then be able to access your shared NTFS partition without problems.

 Thanks Mark, worked a treat

---

