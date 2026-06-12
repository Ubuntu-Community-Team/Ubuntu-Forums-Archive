---
title: "Boot, plymouth d out of memory Nvidia Driver"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by makitso on 2010-05-13
Upgraded to 10.04 with proprietary Nvidia driver.  No plymouth at boot, but dmesg gives error below.  On shutdown get large plymouth display.  Tried several hints but none work.

 2.985912] 1179648 pages RAM
[    2.985914] 951810 pages HighMem
[    2.985915] 149486 pages reserved
[    2.985916] 642 pages shared
[    2.985917] 208097 pages non-shared
[    2.985919] Out of memory: kill process 399 (plymouthd) score 38 or a child
[    2.985920] Killed process 399 (plymouthd)
[    2.987802] ureadahead invoked oom-killer: gfp_mask=0xd0, order=0, oom_adj=0
[    2.987804] ureadahead cpuset=/ mems_allowed=0
[    2.987806] Pid: 398, comm: ureadahead Not tainted 2.6.32-22-generic-pae #33-Ubuntu

---

### Post by morfeasrev on 2010-05-14
Same here on ATi 5850 proprietary drivers.
No plymouth splash screen on boot, but showed on shutdown.

---

### Post by przemo_li on 2010-07-15
Hi, I've got solution for plymouthd here:
[http://forum.ubuntuusers.de/topic/out-of-memory-kills-process-plymouthd-10-04-l/#post-2491201](http://forum.ubuntuusers.de/topic/out-of-memory-kills-process-plymouthd-10-04-l/#post-2491201)

splash file did not existed, create it

---

