---
title: "Install HP DL360 with SmartArray RAID controller boot problem"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by rdepas on 2006-10-22
I have two HP servers. One is a LP2000r and the other is a DL360. Each has a SmartArray RAID controller card in it. Ubuntu 6.06 installs fine but will not boot. Gives a “cpqarray: error sending ID controller” error.

Have researched for quite a while and found many others having the same issue. The only conclusion I am seeing is to recompile the kernel and modify files. My concern with that is when it is time to upgrade the kernel, my system won't boot again without recompiling again. Is there anyone that knows if there is an easy fix for using the SmartArray - or am I stuck with using Suse which works out of the box? :confused: 

Thanks in advance.

---

### Post by plettpc on 2006-10-31
Not neccesary follow this thread #
82466 works like a charm for dapper, I'm still working on 6.10

---

