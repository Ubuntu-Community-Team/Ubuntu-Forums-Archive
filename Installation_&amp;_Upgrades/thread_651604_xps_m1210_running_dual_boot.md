---
title: "xps m1210 running dual boot"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by lenninct on 2007-12-27
i just upgraded my ram to 2 (2 gibs) sticks and system monitor only shows 3.2 gb  insteads of 4 gb any ideas why? do i have to reinstall windows vista and Ubuntu 7.10

---

### Post by bonzodog on 2007-12-28
No, you do not need to re-install. It is showing the right amount of memory, but not very accurately.
To get a true memory reading, open a terminal and type:
```
free -m
```.
That will give you a true memory usage and availability count in megabytes.
I think the 3.2GB memory has to do with calculating space as it gets larger, as it counts it in integers.

---

### Post by lenninct on 2007-12-28
thx , read a lot of posting and sites saying that this is a 32 bit os problem, so i guess that i been had, should have done my research before buying this ram, but hey it runs a lot better now, 

vista boot from 40 secs to under 12 secs and ubuntu i have yet to time it.

---

