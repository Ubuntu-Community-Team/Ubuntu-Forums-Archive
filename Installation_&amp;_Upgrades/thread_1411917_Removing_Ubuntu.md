---
title: "Removing Ubuntu"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by BlackMaxPhoto on 2010-02-20
I just installed 9.10 as a Win7 dual boot and would like to REMOVE it.

The cable connection will not work from the install, works from the live CD but not the install.

What's a SAFE way to remove Ubuntu from the machine?

BC

:confused:

---

### Post by darkod on 2010-02-20
Boot windows and open Disk Management. Delete the ubuntu partitions. Use that space for a ntfs partition or how ever you like.
Restore windows bootloader on the MBR using your win7 dvd or if you don't have one get a rescue cd here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Instructions to restore the bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by BlackMaxPhoto on 2010-02-20
As a precaution I did the MBR repair FIRST, but thanx

BC

:popcorn:

---

### Post by darkod on 2010-02-20
Works that way too. :)

---

