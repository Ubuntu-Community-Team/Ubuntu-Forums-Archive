---
title: "Error when running modprobe ndiswrapper"
date: 2005-10-11
forum: Installation &amp; Upgrades
---

### Post by dizbah on 2005-10-11
I tried to install 2 wireless cards and get my wireless light to come on.  My problem is getting the following:


 modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-686-smp/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted



Suggestions plz :)

---

### Post by Zelut on 2005-10-11
I had that same issue once.  It looks like you're using a different kernel version but that was my issue.  I updated the kernel from 2.6.10 to 2.6.12 and then it seemed to work... it did seem like an odd issue though, I don't know if that'll solve your problem or not.

---

### Post by dizbah on 2005-10-13
it has not.  any ideas?

---

