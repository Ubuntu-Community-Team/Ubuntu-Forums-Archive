---
title: "Adding a new partition to an ntfs disk"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by chris_tikva on 2008-08-08
I'm trying to install ubuntu to the computer internal disk which is a single ntfs partition of 120G but can't find how. A poke around told me that gparted can't do anything with ntfs other than detect it. Is there another tool which can be used?

On a follow up question, assuming that I can create a nice new partition, can I simply copy the file system off my external drive implementation of ubuntu or do I need to start from scratch with the live CD?

Thanks,

Chris

---

### Post by logos34 on 2008-08-08
Gparted should be able to resize it.  But if this is Vista, use it's own disk management tool to shrink it.

2.  you can clone the external partition to the internal.  But the destination partition has to be same size.
Use gparted copy/move feature or the dd command.  You'll obviously have to install grub to the mbr or else use windows bootloader to chainload ubuntu

---

### Post by chris_tikva on 2008-08-08
I tried gparted but I get an orange triangle with ! in it and all the options apart from "delete" are greyed out. I looked at the "show features" list and it had big crosses all along the ntfs line apart from detect. This is gparted 0.3.5, is there a better version? 

The disk is XP.

Thanks,

Chris

---

### Post by logos34 on 2008-08-08
boot back into xp and defrag several times.  

Follow [this guide]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html") (applies to desktop as well).  Then try gparted again.

---

