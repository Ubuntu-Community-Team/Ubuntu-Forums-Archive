---
title: "Upgrade with /home partition"
date: 2013-11-05
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2013-11-05
Could someone point me to a help file or tutorial to upgrading with a separate /home parition.  I currently have 12.10 on one partiton and my home directory on another.  I would like to install the new version (or Kbuntu, or others) on different partitions, how is this done.

How is the switch made to which version and or flavor...  at grub....  I had a terrible time with this when doing the dual book win8/12.10.....

d

---

### Post by oldfred on 2013-11-06
You mention Windows 8. Is this a UEFI system?

Good backups are always a good idea.
You should use manual install or something else and choose current / (root) for new root, format as ext4, also choose current /home partition and mount as /home but DO NOT format it or it will erase all your data. If swap exists it should find it and reuse it.

---

### Post by claven123 on 2013-11-06
Yes, it's a UEFI system.
I see conflicting information....

I  guess I will do a back up then...  do the install.

I guess your directions are a bit confusing.  I would like to keep my current root the same (it's on it's own partition), but it's not clear as to how to do this.  And install the new version over top of the old 12.10 version. 

This shouldn't mess with grub and all that mess I had back then...


D

---

### Post by oldfred on 2013-11-06
Similar instructions.
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

You click on the change box and choose the partition you want to reuse. This is where I over installed Saucy.

---

