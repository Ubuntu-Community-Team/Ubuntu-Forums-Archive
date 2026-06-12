---
title: "Move ubuntu (i have dual boot thing) to another partition."
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by tamaskan on 2012-10-31
Hi,
I would like to move ubuntu from (C:/)[OS] to (D:/) and I also want to ask if this work? And if I wanted to move(maybe re-install), I wonder if there are 32-bit ubuntu?

Thanks in advance! :P

---

### Post by darkod on 2012-10-31
Do you have wubi inside windows, or ubuntu? Windows calls C and D only ntfs partitions and ubuntu doesn't install on ntfs so you probably have wubi.

I don't use wubi so I can't help much with moving it to another partition.

---

### Post by tamaskan on 2012-10-31
oh, yes I use wubi, is not the same as ubuntu?

---

### Post by darkod on 2012-10-31
The OS is the same but the way it's installed is not. Wubi is like virtual ubuntu inside windows.

That is not a proper dual boot where ubuntu is on it's own partition.

---

### Post by oldfred on 2012-10-31
More info on wubi.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

If you have found you like Ubuntu then it may be time to do a full partitioned dual boot.

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
> Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.


HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

---

