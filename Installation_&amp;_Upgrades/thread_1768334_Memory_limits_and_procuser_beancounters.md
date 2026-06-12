---
title: "Memory limits and /proc/user_beancounters"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by nboutelier on 2011-05-26
Is my webhost dicking me around and not allowing me to use the advertised 4GB of memory or am I missing something?
 
While trying to allocate 500MB of shared_buffers to postgresql I got
an error stating theres only 400MB available on the system.

Changing kernel.shmmax didn't affect the 400MB limit.

I checked /proc/user_beancounters and noticed that there is a
120,000 barrier & limit for shmpages and that im currently at 119,496
with a failcnt of 9,599. kmemsize shows a barrier of 456,000,000 and
im using about 22,400,472.

Heres the cat /proc/user_beancounters
uid resource held maxheld barrier limit failcnt
70160: kmemsize 22400472 22592609 456000000 480000000 0
lockedpages 0 0 4800 4800 0
privvmpages 167191 167952 1344800 1415577 0
shmpages 119942 119942 120000 120000 9569
dummy 0 0 9223372036854775807 9223372036854775807 0
numproc 50 50 2400 2400 0
physpages 82048 82365 0 2147483647 0
vmguarpages 0 0 1048576 2147483647 0
oomguarpages 82048 82365 9223372036854775807 2147483647 0
numtcpsock 8 9 8000 8000 0
numflock 2 2 1000 1100 0
numpty 1 1 200 200 0
numsiginfo 0 1 1024 1024 0
tcpsndbuf 140032 157536 40000000 80000000 0
tcprcvbuf 131072 147456 40000000 80000000 0
othersockbuf 9312 9312 20000000 40000000 0
dgramrcvbuf 0 6984 40000000 40000000 0
numothersock 14 14 8000 8000 0
dcachesize 504243 512694 114000000 120000000 0
numfile 2491 2500 160000 160000 0
dummy 0 0 0 0 0
dummy 0 0 0 0 0
dummy 0 0 0 0 0
numiptent 14 14 500 500 0

---

