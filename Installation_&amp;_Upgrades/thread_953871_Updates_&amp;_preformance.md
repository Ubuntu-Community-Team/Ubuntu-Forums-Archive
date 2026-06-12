---
title: "Updates &amp; preformance"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by steelrealm on 2008-10-20
Hey everyone,

I'm relatively new to the Linux and Ubuntu communities.  After some time playing with multiple Live CD's I decided it was time to actually install a distrobution onto my secondary Harddrive.

I'm running on an older machine and have Windows XP running fine on the other harddrive(Dualboot).  Specs are as follows:

P4 1.7GHz Proccessor
512mb RAM
240mb swap

So..  I booted up the live CD I'd just burned for Xubuntu and formatted the harddrive.  I installed the OS seemingly without a hitch.  I was greeted with 110 important or recommanded updates.  I installed them all...

Unfortunately I didn't take the time to look at my systems preformance before the updates but my system currently runs at anywhere from 5-40% of CPU's total when idle/switching windows and with 200mb of RAM (all the way up to 300 when doing very little).

I was just wondering if maybe there was something wrong with these numbers, and if so what I could do to lower them.
Is it possibly all the gnome / gkt updates I just are bogging down the system?

I choose Xubuntu because I thought it would work well on my hardware, but as is, my computer is running slowly on Xubuntu and r
eaches 100% CPU regularly.  I am VERY worried about the well being of the machine (being old, and my only one) and if theres anything I can do to lower the CPU load I would love to know.

Thanks!

---

### Post by cariboo on 2008-10-20
Depending what is running in the background that is completely normal. I don't know how you are checking memory and cpu usage, but the gui tools always seem to add a bit of overhead. Open a terminal and run:

```
top
```

to view processes running and memory usage.

It is normal for linux to use almost all your ram, it keeps programs cache in ram until they are needed, or if another process needs more ram the cached programs get removed.

This is the result of:

```
free -m
```

on my computer, have have 2Gb ram and I'm only running Firefox and downloading a legal torrent:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          1976       1952         24          0         34       1392
-/+ buffers/cache:        526       1450
Swap:         5530          5       5524
```

Jim

---

