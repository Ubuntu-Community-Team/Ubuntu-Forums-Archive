---
title: "problem in `apt-get source --compile libkolabxml1v5`"
date: 2017-01-31
forum: Installation &amp; Upgrades
---

### Post by wisekaa03 on 2017-01-31
```
root@mail-01:~# apt-get source --compile libkolabxml1v5
Reading package lists... Done
Picking 'libkolabxml' as source package instead of 'libkolabxml1v5'
Skipping download of file 'libkolabxml_1.2~dev20160330.orig.tar.gz' as requested hashsum is not available for authentication
Skipping download of file 'libkolabxml_1.2~dev20160330-0~kolab1.diff.gz' as requested hashsum is not available for authentication
Need to get 1,152 B of source archives.
Get:1 http://obs.kolabsys.com/repositories/Kolab:/Winterfell/Ubuntu_16.04 ./ libkolabxml 1.2~dev20160330-0~kolab1 (dsc) [1,152 B]
Fetched 1,152 B in 0s (5,124 B/s)
W: Can't drop privileges for downloading as file 'libkolabxml_1.2~dev20160330-0~kolab1.dsc' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)

```

why ?

---

### Post by Perfect Storm on 2017-01-31
properly it need superuseer access. do a **sudo** infront.

---

