---
title: "Seperate home partition guide"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by pinkpanther_bc on 2007-10-02

Looking for a "good" guide to move my home to a different partition?
Have made the partition but want to know the steps to move my current home directory to the new partition. Did follow one guide but that failed. So if some one can help with a guide that works that would be great! Running Gutsy beta

---

### Post by forestpixie on 2007-10-02
see [this]("http://www.psychocats.net/ubuntu/separatehome") one refered to a lot

---

### Post by pinkpanther_bc on 2007-10-02
Ok will give that a go this evening. Would be nice if someone have tried this already and had success.

---

### Post by pinkpanther_bc on 2007-10-02
fstab> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bf54a21f-39af-4eca-8787-1d1d04c003d9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=689fa8ae-41af-4c35-b1e4-caf365ba269e /media/sda3     ext3    defaults        0       2
# /dev/sda5
UUID=c96a4ca6-41ec-4f2c-91cd-54076eb2aca2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

have been following this thread  [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)
and what would be the correct info for my /dev/sda3 in fstab

---

