---
title: "Software Raid 0"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by Trekster on 2008-11-14
Hi,

I'm trying to setup software raid on Ubuntu for the first time. I want to setup two 1TB harddrives in RAID0. 

For testing purposes i'm trying it out on vmware to see how everything is setup before i begin. I tried searching and there are a lot of guides for RAID1 configurations, however very little if any on RAID0, but the basic principles are the same. 

I have however run into a problem. During the partitioning of the drives i select the two drives and make two big partitions on both drives. After that i setup software RAID0 and everything appears to be ok. It makes one big partition which i then delete and try to create a swap and a / partition. Here i run into problems, when i create the first partition the rest of the drive is marked "unusable"...how come? Can i only make one big partition?

I'm used to FakeRaid on Windows machines but it was a pain(actually could not get it to work on 8.10) so i decided sw raid was a good alternative, maybe even better.

---

### Post by inobe on 2008-11-14
hi, have you checked the wiki ?

notice method 1 in the link

[https://help.ubuntu.com/community/FakeRaidHowto#Method%201](https://help.ubuntu.com/community/FakeRaidHowto#Method%201)

it mentions the use of the alternative cd.

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

have you tried it.

---

### Post by Trekster on 2008-11-14
> **inobe said:**
> hi, have you checked the wiki ?

notice method 1 in the link

[https://help.ubuntu.com/community/FakeRaidHowto#Method%201](https://help.ubuntu.com/community/FakeRaidHowto#Method%201)

it mentions the use of the alternative cd.

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

have you tried it.


Yes i tried it and it worked to the point where the install went through but when trying to boot it would hang for about 30s and throw me to the busybox. Where it threw something like "ALERT! /dev/mapper/xxxx_xxxx does not exist" or something to that effect. Using dmraid i could see the drives and RAID array just fine though...I even tried setting rootdelay=130 as suggested in another post here.
well needless to say after tinkering with it for about 3 hours last night i gave up and decided to try software raid this morning, but have run into the above mentioned problem :(

I've added a screenshot of my problem.

---

### Post by Trekster on 2008-11-14
Nevermind, i figured it out :-)

I must be tired from going late to sleep last night, but the guide had a little line that i must have missed

"In Linux software RAID each mount point is usually configured as a separate RAID device"

:)

---

### Post by inobe on 2008-11-14
would you mind creating a howto article someday ?

i haven't been here long and it seems to be popular :)

---

