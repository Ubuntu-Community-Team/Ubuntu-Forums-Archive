---
title: "what is a good file system for ubuntu linux??"
date: 2006-09-14
forum: Installation &amp; Upgrades
---

### Post by mfaheypride on 2006-09-14
Hi,i was wondering, what is a good file system to use, ext2, ext3, fat32, hfs what should i use for my ubuntu install?

---

### Post by mitch.c on 2006-09-14
Depends on partition, filesystem size, and personal taste. Generally speaking, if you don't know the pros and cons... ext3 if you are a linux only system, vfat or ntfs only for partitions that you want Windows (dual-boot) to see. But linux partitions should definitely be a linux specific type like ext2, ext3, reiser, etc.

---

### Post by mfaheypride on 2006-09-14
> **mitch.c said:**
> Depends on partition, filesystem size, and personal taste. Generally speaking, if you don't know the pros and cons... ext3 if you are a linux only system, vfat or ntfs only for partitions that you want Windows (dual-boot) to see. But linux partitions should definitely be a linux specific type like ext2, ext3, reiser, etc.

thx for the help, im dual booting but i dont need windows to see it, so im using ext3 thx

---

### Post by szf on 2006-09-15
You've made a good choice with ext3 then... don't let 'em tell you different.

---

