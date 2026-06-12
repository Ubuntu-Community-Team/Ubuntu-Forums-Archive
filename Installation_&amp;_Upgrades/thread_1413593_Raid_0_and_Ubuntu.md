---
title: "Raid 0 and Ubuntu"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by rankchipmunk on 2010-02-22
After a long time of trying different things I am stumped. I have a new computer with two 500 gb hard drives which I use in raid 0. I tried to install Ubuntu 9.10 off the live cd but it was unable to partition the raid and kept failing. I was then told top use the alternate cd. I use that and my raid is detected, partitioned, and the system is installed. However now I cannot install a boot loader as I get continuous errors. Right now I am left with no ideas with what to do. I have Ubuntu installed to my hard drives just no way of accessing it.

---

### Post by darkod on 2010-02-22
If you boot the live desktop and run:

ls -l /dev/mapper/

does it show your array name?

---

### Post by RTrev on 2010-02-22
If you're using software RAID, you need to create a /boot partition which is *not* part of your RAID-0 array.  This array has not yet been assembled at boot time.

Make sense?

---

