---
title: "ubuntu 16.04 high memory usage"
date: 2016-04-21
forum: Installation &amp; Upgrades
---

### Post by archish2 on 2016-04-21
Fresh install and boot, ram usage is about 1 GB. Anyone else facing this issue? Previous release of ubuntu hovers around 450 MB.


[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1572801](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1572801)

Cheers,

---

### Post by sgian on 2016-04-21
I just noticed it too and confirmed the bug on the launchpad link.

---

### Post by squilookle on 2016-04-21
I have also noticed this. 15.10 used about 700mb on fresh boot, 16.04 is using just over 1GB

---

### Post by yoshii on 2016-04-21
damn, that's discouraging.  Are you guys using 32-bit or 64-bit ?

---

### Post by squilookle on 2016-04-21
64 bit. I must say the system is very responsive and CPU usage looks a little low, it's hovering around 0-1% which is good. 

The memory usage is higher than I would like to see it but I have plenty so it's not a huge problem for me. 

Compiz seems to be taking the most memory so I wonder if it is related to graphics, which is apparently Intel Ivybridge Mobile on this laptop, Incidentally, I've tested some HD video and it looks stunning, much smoother and less screen tearing than I've seen previously so it's actually pretty good so far.

---

### Post by slickymaster on 2016-04-21
*Moved to ***Installation & Upgrades*** sub-forum*

---

### Post by Aeglius on 2016-05-18
I also noticed significant higher memory usage (almost twice, with a single IDE and a browser my 8GB are full!).

I have been observing my RAM usage for some time (suffering from bug [#1518457]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1518457")), and I have two observations:


[LIST=1]
[*]When I sum up all RAM usage of individual applications as listed in gnome-system-monitor, the sum is significantly less then the total RAM usage. I can not identitfy any single application or process that has suspiciously higher usage than in 15.10.
[*]The mentioned bug caused my computer to lock up when total used RAM reached around 60% of total available RAM. Now it reaches almost >90%.
[/LIST]
I am not expert with the different memory measures (and I know it's not additive since applications share memory).
But my guess is that the measure what gnome-system-memory (or the underlying tools) outputs changed.

---

### Post by richard-stabler on 2016-07-05
I have seen this too. Apparent usage does not explain the 17.1G (55% use). Compiz constantly spinning the processors and has highest RAM usage.

              total        used        free      shared  buff/cache   available
Mem:            31G        1.8G         10G         15G         18G         13G
Swap:           31G          0B         31G

A lot of stuff seems to be stuck in shared buff/cache?!?!?!

---

### Post by Impavidus on 2016-07-05
According to the manual for **free**:```

DESCRIPTION
       free  displays the total amount of free and used physical and swap mem&#8208;
       ory in the system, as well as the buffers and caches used by  the  ker&#8208;
       nel.  The  information  is  gathered by parsing /proc/meminfo. The dis&#8208;
       played columns are:

       total  Total installed memory (MemTotal and SwapTotal in /proc/meminfo)

       used   Used memory (calculated as total - free - buffers - cache)

       free   Unused memory (MemFree and SwapFree in /proc/meminfo)

       shared Memory used (mostly) by tmpfs (Shmem in /proc/meminfo, available
              on kernels 2.6.32, displayed as zero if not available)

       buffers
              Memory used by kernel buffers (Buffers in /proc/meminfo)

       cache  Memory  used  by  the  page  cache and slabs (Cached and Slab in
              /proc/meminfo)

       buff/cache
              Sum of buffers and cache

       available
              Estimation of how much memory  is  available  for  starting  new
              applications,  without swapping. Unlike the data provided by the
              cache or free fields, this field takes into account  page  cache
              and also that not all reclaimable memory slabs will be reclaimed
              due to items being in use (MemAvailable in /proc/meminfo, avail&#8208;
              able on kernels 3.14, emulated on kernels 2.6.27+, otherwise the
              same as free)

```(Use **man free** too read for yourself.)

There's no stuff stuck in buff/cache, the stuff (most of it, at least) simply remains there until the memory is needed for something else.

---

