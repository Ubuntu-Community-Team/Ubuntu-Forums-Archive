---
title: "Cannot start Apache2 after upgrade to 12.04"
date: 2012-07-26
forum: Installation &amp; Upgrades
---

### Post by holobeat on 2012-07-26
I've just upgraded to 12.04 and now I cannot start Apache2. This is the syslog: 

Jul 26 14:11:56 gosfcs kernel: [ 9037.776698] apache2[6307]: segfault at 0 ip 00007fc471978626 sp 00007fff1a78dd38 error 4 in libc-2.15.so[7fc471848000+1b3000]

My system is:

Ubuntu Linux 12.04
Linux 3.2.0-27-generic on x86_64
Intel(R) Xeon(R) CPU E5620 @ 2.40GHz, 8 cores
Zend Server 5.6.0

---

### Post by DJ_Max on 2012-07-26
Did you install Apache from source?

---

