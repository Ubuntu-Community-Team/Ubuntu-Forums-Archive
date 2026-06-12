---
title: "linux-686-smp can't see all my RAM"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by atomSmith on 2006-08-16
I installed Ubuntu Desktop on my Intellistation Z Pro (dual Xeon), with 8GB ram, and upgraded the kernel to linux-686-smp (and no errors were reported).

/proc/cpuinfo shows the correct # of CPUs

/proc/meminfo shows 3759432 KB ram (a weird amount)

When I boot, the bios shows the correct 8192 MB.
When I run MemTest86 3.2, it shows the correct 8192 MB, and reports no errors in the RAM (I ran the whole thing).



What's going on ?

---

### Post by Klaidas on 2006-08-16
Woah, 8GB of RAM.
I'm not a expert in these things, but you might need to recompile your kernel and enable support for that much RAM 
[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)

However, someone should verify this.

---

### Post by patrickfromspain on 2006-08-16
I also thing you'll have to recompile the kernel in order to get the 8 gigs detected. I quite sure ubuntu is compiled as to use 3 gigs for userspace and 1 for the kernel or something like this.

---

### Post by atomSmith on 2006-08-16
:) Yes!  That worked.  Thanks for the link!

I also saw some other non-default options I needed.

(I'm doing some scientific number-crunching, so I need a LOT of ram)

---

