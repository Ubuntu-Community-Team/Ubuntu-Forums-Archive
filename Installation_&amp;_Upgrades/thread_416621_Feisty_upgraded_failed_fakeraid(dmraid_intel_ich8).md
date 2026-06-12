---
title: "Feisty upgraded failed fakeraid(dmraid intel ich8)"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by zero-Q on 2007-04-21
hi, I have been using edgy on fakeraid partition and but after upgraded to feisty my system was broken. and on the other hand I tried clean install but after install dmraid, I could not see the partition table, is feisty or dmraid+feisty bugged about fakeraid? is there anyone having upgrade problem with fakeraid? or is there anyone solving the problem????

---

### Post by zero-Q on 2007-04-21
when I type "dmraid -ay" in terminal that errpr message appears :
root@ubuntu:~# dmraid -ay
ERROR: isw device for volume "Volume0" broken on /dev/sda in RAID set "isw_cgffbhhfed_Volume0"
ERROR: isw: wrong # of devices in RAID set "isw_cgffbhhfed_Volume0" [1/2] on /dev/sda

---

### Post by stevecs on 2007-04-21
yeah, I got this same error w/ my ICH7R on the P5W64WS Pro MB.   I just ended up using meta devices for a software raid.

---

