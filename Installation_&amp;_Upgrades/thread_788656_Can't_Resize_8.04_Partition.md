---
title: "Can't Resize 8.04 Partition"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by snow_56767 on 2008-05-09
Hi,
   I've Installed 8.04 LTS and I have just noticed that a VM(Virtual Machine) and Wine will not play windows games. So I have decided that I should dual boot 8.04 LTS and Windows XP SP2. But GNU Parted 1.7.1 Will not let me resize my partition. Every time I try to I get an error saying:
```
Error: File system has an incompatible feature enabled.
```
Is there a way to disable the incompatiblity feature, or do I have to Install windows first then linux?

---

### Post by Patb on 2008-05-10
Snow, I'm not sure whether this is the cause of your problem but you cannot resize a partition which is already mounted.  Try booting a live CD and see if you can use gparted from there.  

Cheers, Pat.

---

### Post by snow_56767 on 2008-05-10
Hi,
   I tried using the Live CD, It didn't work. I still got the same error. Which is:
```
Error: File system has an incompatible feature enabled.
```

---

### Post by Pumalite on 2008-05-10
Get Gparted Live CD and do all your partitioning from there.

---

