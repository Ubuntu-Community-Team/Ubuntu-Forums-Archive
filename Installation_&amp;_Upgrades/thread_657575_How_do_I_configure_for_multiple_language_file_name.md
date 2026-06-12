---
title: "How do I configure for multiple language file names"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by robertmk on 2008-01-03
Hi,

I want to keep the system and all the users using en_US.utf8, but I have files with Thai names that I need to bring into the system.  Depending on the software I use to copy, I either get an error that says "Failed to convert command to 8 bit charset" or all the Thai characters get changed to question (?) marks.  Neither of these are desirable.

The drive where I want to store these files has the following entry in fstab:
/dev/mapper/lvm--raid-lvm0 /store1  ext3  defaults 1  2

locale -a results in:
C
en_US.utf8
POSIX
th_TH.utf8

Help is greatly appreciated.

Thanks,
Robert :~)

---

