---
title: "how to add cpufreq support?"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by jstateson on 2008-09-13
I swapped out a pair of MP-2200 cpu's for a pair of 2800+ mobile barton cores.  They boot at 1866 but can run much higher.  powernowd and cpufrequtils are installed but it seems i am missing the cpufreq driver.

root@jyslinux4:/home/jstateson# cpufreq-selector -g performance
No cpufreq support

Googleing I see where the kernel needs to have cpufreq support and a driver powernow-k7 is needed.  I do not know enough about configuring ubuntu kernels to do this. 

====the following occures when I run powernowd=====

root@jyslinux4:/home/jstateson# powernowd
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
/sys/devices/system/cpu/cpu0/cpufreq/affected_cpus: No such file or directory
powernowd: err=2
powernowd: Found 2 scalable units:  -- 1 'CPU' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   (for example: powernow-k7), and that it works. Check
   'dmesg' for errors.
If all of the above are true, and you still have problems,
please email the author: xxxxx

It would be nice if I could find a walkthru to rebuild the kernel (if needed).

I have two other systems that run fine with mobile-xp cpu's but the OS is windows and I am using crystalcpuid.  This is my first linux system with mobile cpu-s.

..thanks..

---

