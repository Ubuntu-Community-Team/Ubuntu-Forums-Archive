---
title: "windows dual install"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by brw314 on 2010-03-17
Hi,

I have a pc with windows on it, about 90% of the hard drive is full. I want to install dual
boot ubuntu with ubuntu using about 70% of the hard drive, do I need to manually create space, or can I just set during the install will ubuntu just over-write that much. I don't care about the files i have under windows.

Thanks
Brian

---

### Post by oldfred on 2010-03-17
I do not think it will let you shrink the partition smaller that the data to prevent you from destroying something you want. Shrinking/moving also goes faster when most of the space is empty. You should delete data and defrag twice before shrinking the partition.  Windows needs 10-20% free space to keep working.

If you have XP you can use gparted, but if Vista or 7 you need to use the windows tools to shrink the windows partition. It is best to shrink partition and reboot windows to make sure it works with the new size. It usually want to run some chkdsk or other repairs after partition changes.

---

