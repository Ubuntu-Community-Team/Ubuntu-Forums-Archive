---
title: "re-partitioning"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by frankdn on 2008-05-12
The live CD install creates only one partition for ubuntu, and I'd like to split that in two, so that my home directory lives in a partition of its own.

What's the safest tool to use for that-- GParted, maybe?

---

### Post by Pumalite on 2008-05-12
Go Manual and make 3 'New' partitions:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops for hibernation)
The rest for /home
The installer will do the rest after you press 'Forward'

---

### Post by ubunny on 2008-05-12
however this leads to another question later on, which is where I am ;)

can I use qparted to safely resize the /home partition from available space in the / (root) partition?  /home is filling up quickly.

do I need to defragment the drive?   and if so, which linux/ubuntu tool would be recommended?

Cheers

---

### Post by Pumalite on 2008-05-12
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

