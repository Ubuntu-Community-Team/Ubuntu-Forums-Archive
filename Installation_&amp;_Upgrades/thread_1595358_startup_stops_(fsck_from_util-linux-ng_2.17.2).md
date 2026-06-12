---
title: "startup stops (fsck from util-linux-ng 2.17.2)"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by wthpr0 on 2010-10-13
i get this when i'm trying to boot up my ubuntu-server 10.04:

```
fsck from util-linux-ng 2.17.2
/dev/sdb1: rent, 393604/4685824 files, 9517114/18738176 block
``` 

I can boot up fedro live cd and chroot into the ubuntu-server 10.04 install. The error arose when I go a sudden power interuption.

please anyone i can't boot up my server at all and I really need it for a school project :(.

---

### Post by nashjc on 2010-10-14
I don't have a solution, but you are not alone. Had this happen to me today. One total reinstall so far -- not good. Seems to be related to power management according to [http://superuser.com/questions/112848/ubuntu-nbr-karmic-boot-freezes-at-fsck-from-util-linux-ng-2-16](http://superuser.com/questions/112848/ubuntu-nbr-karmic-boot-freezes-at-fsck-from-util-linux-ng-2-16)

jn

---

### Post by nashjc on 2010-10-14
Actually booted Knoppix and removed reference to USB drive (not powered on) in /etc/fstab and things worked again. 

JN

---

