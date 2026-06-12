---
title: "Using DEADLINE scheduler"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wnelson on 2009-09-23
[https://lists.ubuntu.com/archives/karmic-changes/2009-September/009320.html](https://lists.ubuntu.com/archives/karmic-changes/2009-September/009320.html)

A change to the deadline scheduler with the new kernel update.

---

### Post by Longinus00 on 2009-09-23
Any good benchmarks on this? Too much gets updated at a time on my computer to reliably compare bootcharts.

---

### Post by MacUntu on 2009-09-23
You can change the I/O-scheduler via the kernel boot parameter 'elevator'. To compare just add 'elevator=cfs' or 'elevator=deadline' to the kernel line of the GRUB menu entry.

---

### Post by novafluxx on 2009-09-23
> **MacUntu said:**
> You can change the I/O-scheduler via the kernel boot parameter 'elevator'. To compare just add 'elevator=cfs' or 'elevator=deadline' to the kernel line of the GRUB menu entry.

Had no idea it was that easy! I can't wait to test this out! Thank you!

---

### Post by lazka on 2009-09-23
You can also change it on the fly @ /sys/block/sdX/queue/scheduler

Deadline is much better on my system.. I can backup to my external HD _and_ work at the same time now.

It might be worse for other workloads.. but at least there are no 10 seconds desktop freezes anymore.

---

### Post by novafluxx on 2009-09-23
I really need to learn more about Linux... things like this that aren't the default that I can change in order to have my system work how I want it.
 
Great info in here, I'm gonna have to give it a shot tonight. I always though the scheduler was chosen during the compiling of the kernel and couldn't be changed. I guess I was incorrect!:guitar:

---

### Post by novafluxx on 2009-09-24
How do I check which scheduler I'm running? I assume there's a command for that :-)

---

### Post by MacUntu on 2009-09-25
```
cat /sys/block/<disk>/queue/scheduler
```
Where <disk> is the hard drive to check (eg. sda).

---

