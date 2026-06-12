---
title: "Clean install, mounting x2 fat32 and linux/swap"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by circadianhelix on 2006-06-09
Having some trouble find info related to this,  im doing a clean install of ubuntu-desktop 6.06 (by clean i mean using the install to wipe xp).
I'm attempting to use 2 fat32 partitions (root & /home) and the linux swap.
Once i try to install it tells me: creating Fat32 file system for /home in partition #3 of IDE1 master (hda)
error : Invalid file system for this mount point

Im tempted to do a standard install hopefully its nothing major. (ext3 works fine, maybe need that for root)?

---

### Post by Sutekh on 2006-06-09
[quote=circadianhelix]Having some trouble find info related to this,  im doing a clean install of ubuntu-desktop 6.06 (by clean i mean using the install to wipe xp).
I'm attempting to use 2 fat32 partitions (root & /home) and the linux swap.
Once i try to install it tells me: creating Fat32 file system for /home in partition #3 of IDE1 master (hda)
** error : Invalid file system for this mount point**

Im tempted to do a standard install hopefully its nothing major. (ext3 works fine, maybe need that for root)?[/quote]
That's crazy talk :) 

Even the installer knows using FAT formatting for your Linux system is doomed to failure.  FAT filesystems don't support the permissions that are part and parcel of GNU/Linux.

You should be using ext3 filesystems for all your Linux partitions.  

The only reason you may wish to use a FAT partition is for sharing data between Ubuntu and Windows, but if you are wiping Windows, then leave the FAT partitions in your wake when you install.

---

