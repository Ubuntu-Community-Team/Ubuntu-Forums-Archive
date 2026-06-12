---
title: "change to SSD without re-install of Ubuntu"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by kornelix on 2010-12-26
I recently moved my Ubuntu 10.10 partition from a rotating disk to a solid state disk. I copied the partition using parted-magic. It works fine. Booting is slightly faster and loading large executables is much faster. 

I have a related question: when Ubuntu is initially installed, are any configuration parameters being set that would remain incorrect (or not optimal) after a hardware change (graphics card, SSD, xxx)? In this case, should I re-install Ubuntu on the SSD?

thanks

---

### Post by dino99 on 2010-12-26
ubuntu use uuid to boot ( grub menu), so if that device have changed, that mean a new uuid too and so you need to update-grub

sudo blkid
( let you know uuids)

---

### Post by kornelix on 2011-01-01
That has nothing to do with my question, but thanks anyway.

---

### Post by kornelix on 2011-01-01
I went ahead and re-installed Ubuntu on the SSD. This reduced the boot time from 18 to 14 seconds. I have no idea why. I then moved the partition using gparted. Everything worked perfectly, and the boot time went back to 18 seconds. I have no idea why.

---

