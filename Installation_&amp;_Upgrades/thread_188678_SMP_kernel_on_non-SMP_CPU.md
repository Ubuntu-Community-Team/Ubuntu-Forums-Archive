---
title: "SMP kernel on non-SMP CPU"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by migster85 on 2006-06-04
Hello,

I have a Pentium 4 3.4GHz HT processor, not SMP, and after upgrading to 6.06 from 5.10 "cat /proc/cpuinfo" shows that I have 2 CPUs now. Can the new 686 SMP kernel recognize that I don't have an SMP machine?

I made a fresh install (without an upgrade) onto my laptop, which is also a P4, and there the same kernel only shows one CPU in /proc/cpuinfo... Any ideas how I can fix this?

Thanks,
Max

---

### Post by taurus on 2006-06-04
Wait a second!!!  If you have P4 with HT, then you can use the linux-i686-smp then...  Therefore, "cat /proc/cpuinfo" SHOULD report that you have two CPUs, CPU0 & CPU1.  The one on your laptop is an over version of P4 (NO HT) so of course, it sees it as one CPU...  

I have P4 3.0GHZ with HT on my desktop and I use i686-SMP for it but I have a laptop with P4 2.4GHz and I only use i686 for it...

---

### Post by migster85 on 2006-06-04
wow, i feel like a complete idiot... i've been using this HT CPU all this time (2 years) without HT support... I thought SMP was only for multiple CPUs and dual cores!! *cries and runs away*

So, now that "I" have this "fixed", when compiling code with gcc or gpp, should I enable some options during compile time to run with HT?

Thanks,
Max

---

