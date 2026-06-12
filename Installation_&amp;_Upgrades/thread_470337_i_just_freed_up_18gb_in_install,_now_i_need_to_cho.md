---
title: "i just freed up 18gb in install, now i need to choose...???"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by doobey on 2007-06-10
I am giving 16gb for 7.04. do I choose primary or logical? beginning or end? ext3? mount point = ?

also same for the 2GB for the swap file.


THANKS!!!

---

### Post by logos34 on 2007-06-10
> **doobey said:**
> I am giving 16gb for 7.04. do I choose primary or logical? beginning or end? ext3? mount point = ?

also same for the 2GB for the swap file.


THANKS!!!

It's easiest just to make both primaries.  Format root as ext3 with mount point at '/', swap as '/swap'.  If you're using the rile of thumb of making swap file twice the size of ram, you're wasting space...you'll probably barely ever need it with a gig of ram. You could also add a separate /home partition and make it a logical parition inside an extended partition including /swap (1gb for the latter should be enough)

---

### Post by confused57 on 2007-06-11
> **doobey said:**
> I am giving 16gb for 7.04. do I choose primary or logical? beginning or end? ext3? mount point = ?

also same for the 2GB for the swap file.


THANKS!!!
You can have only 4 primary partitions on a hard drive, if you already have 3 primary partitions...then you would need to make any additional partitions(/ & swap) as logical partitions, which would be within one extended primary partition.

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

