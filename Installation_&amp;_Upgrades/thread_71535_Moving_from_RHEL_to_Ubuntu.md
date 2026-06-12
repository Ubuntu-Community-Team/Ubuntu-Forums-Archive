---
title: "Moving from RHEL to Ubuntu"
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by alterego125 on 2005-10-03
I have a box running centOS 4.1 (RHEL Clone) and I was wondering if it would be possible to upgrade it to Ubuntu without over writing everything. Does anyone know if this is possible and how it could be done.

Regards,

Alterego125

---

### Post by kleeman on 2005-10-03
Depends on how you partitioned your disk for CentOS. If you have all your desired to be preserved data on one or more seperate partitions (/home etc) and the Centos system on another set (/usr / etc) then you should be able to install Ubuntu on your CentOS partitions. The Ubuntu installer allows you to preserve old partitions and mount them where you like (eg at /home). If you have a bunch of desktop related files in your CentOS /home these MIGHT give you a bit of a headache  but it is generally solvable if you have reasonable (non-newbie) linux skills.

---

### Post by alterego125 on 2005-10-04
It looks like my installation is using LVM. It seems to be using my enire hard disk, so my home dir is not seperate. Is there any way around this?

---

