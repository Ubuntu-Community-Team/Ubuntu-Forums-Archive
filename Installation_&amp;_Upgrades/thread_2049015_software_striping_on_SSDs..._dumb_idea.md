---
title: "software striping on SSDs... dumb idea?"
date: 2012-08-27
forum: Installation &amp; Upgrades
---

### Post by dreamgear on 2012-08-27
I bought a new server with a supermicro X9SCL mb, which came with two 128MB SATA SSDs.  Out of the box they were set up as a stripe set.

I just took the defaults as I installed Precise on it, and find that my disk is called /dev/mapper/blahblahblah, indicating this is a "fakeraid" device.

Is there any point in this arrangement ?  Am I getting any improvement in performance for my trouble?   If so, as I understand it the price I pay is a reduction in MTBF, since if either of these devices quit I will need to rebuild.

Thanks in advance for your thoughts.

---

### Post by darkod on 2012-08-27
Well, with raid0 (striping) you get no redundancy. If one disk goes, all the data is gone since you can't recover from the remaining disk.

I am not sure it will decrease SSD life if that's what you are worried about, but I would host any important data on raid0. Of course, you can make regular backups on another medium, and keep working on raid0 if you want to.

---

### Post by dreamgear on 2012-08-28
I guess what I really want to know is there any upside to this?  Will I get improved performance?

---

### Post by shreepads on 2012-08-29
> **dreamgear said:**
> I guess what I really want to know is there any upside to this?  Will I get improved performance?
Depends on what you're running, but from what I can see online, this board only has SATA II support, so if the two 128GB (not MB I assume) SSDs are SATA III capable and capable of saturating a SATA II interface then yes this setup will deliver higher IOPS.

Whether that translates into better performance depends on what you're running.

---

### Post by dreamgear on 2012-08-30
> **shreepads said:**
> Depends on what you're running, but from what I can see online, this board only has SATA II support, so if the two 128GB (not MB I assume) SSDs are SATA III capable and capable of saturating a SATA II interface then yes this setup will deliver higher IOPS.

Whether that translates into better performance depends on what you're running.
Thanks.   Well, I may stop making the MB/GB/TB mistake before I retire.   Took me 20 years to stop saying KB when I meant MB.

---

