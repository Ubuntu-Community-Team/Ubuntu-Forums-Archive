---
title: "Mount NTFS/Installation from a USB stick"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by darkoysm on 2008-03-29
Hey, i've been using this line in the fstab to mount my hard drive:
/dev/hdb1       /media/win      ntfs-3g ro,dmask=0222,fmask=0333 0 0
i've tried modifying it over and over again, but i'm unable to get it mounted with read/write privileges, how can i do that.???

-----------------------------------------------------------------------------------------------------------------------------

The CD drive  on my laptop(compaq nx9010) is malfunctioning, so i cant use to install ubuntu, is there anyway i can do it from my usb drive? if yes, can you provide me with a step by step guide. I found an article about using syslinux, but that didn't work for me, please help.


Thanks
Darko

---

### Post by wolfen69 on 2008-03-29
change ro to rw (**r**ead **o**nly to **r**ead/**w**rite)

---

