---
title: "&quot;Simple Backup&quot; fails after upgrade"
date: 2018-11-17
forum: Installation &amp; Upgrades
---

### Post by John_Rose on 2018-11-17
I was happily using Simple Backup (sbackup package) for several years without problems under 32-bit Ubuntu 12.04 LTS in ext3 format (backing up to an ext3 partition in an external drive). Then about a year ago I updated to Ubuntu 14.04 LTS, and sbackup stopped working. Each time I try to back up (ad hoc full back-up) I get the error **'NoneType' object has no attribute 'st_size'**. Nothing is written in the designated log folder. There is a normally named back-up file, but it is unreadable and shows no properties.
 
  Shortly after upgrading the OS, I added a second user with administrative rights (not used to call sbackup), so I cannot exclude that this is the reason for the failures. I subsequently deleted the second user, but the back-up folder is still mounted in /media/[back-up partition]/[user]/[back-up folder] instead of  /media/[back-up partition]/[back-up folder], but I don't see how this could be a problem.

Perhaps some sort of permissions problem, hope that one of you can help. Thanks and best wishes, John

---

