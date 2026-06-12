---
title: "Upgrade fried my install..."
date: 2013-01-08
forum: Installation &amp; Upgrades
---

### Post by faroutliving on 2013-01-08
I initially created a 11.04 installation last year. I have 2 hardware raid cards on this machine, which at install time I partitioned into 6 partitions on each raid, and then made a software raid 0 out of each matching hardware raid paritions (so sda1 + sdb1 -> md0 basically)

Great performance, but now it is going to bite me in the butt. I upgraded the system to 11.10, and then tried to upgrade to 12.04 (which is where I wanted to get too), but during the 12.04 install it gave me some error and then proceeded to try and undo everything it was doing. It then gave me the error (from memory) "System in a unstable state" to which when it was all done I tried to reboot. And got a flashing cursor. No boot blocks.

So I plugged in another drive and I can see the original 12 partitions (now sdb1->sdb6 and sdc1->sdc6).

Is it possible to recover from this? I'm actually going to put the os on its own SSD and try and keep /user only on the raid, but will I be trying to restore some 72TB! of data?

Where would I go to start learning about what to even do?

Thanks for your help!

Deron

---

