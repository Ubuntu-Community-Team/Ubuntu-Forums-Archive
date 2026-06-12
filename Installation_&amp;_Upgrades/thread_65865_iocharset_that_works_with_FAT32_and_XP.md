---
title: "iocharset that works with FAT32 and XP"
date: 2005-09-15
forum: Installation &amp; Upgrades
---

### Post by kaaredyret on 2005-09-15
I have a shared drive (FAT32) for file sharing between Windows XP and Hoary, but Danish letters are a problem. Danish letters entered in Ubuntu are gibberish to XP, and danish letters entered in XP are "invalid encoded" or something accoring to Ubuntu.

In /etc/fstab I add:

/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

I guess that **iocharset=utf8** is where I should change utf8 to something else, but what? ISO something numbers something?

---

### Post by axrj on 2005-09-15
Try with "utf8" only, remove "iocharset=".

---

