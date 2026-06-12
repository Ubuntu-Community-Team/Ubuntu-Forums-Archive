---
title: "Synatpic/Apt-Get Kernel way below running kernel."
date: 2006-05-04
forum: Installation &amp; Upgrades
---

### Post by general_error on 2006-05-04
I made the mistake of doing an upgrade on my box today using the Synaptic Package Manager and now everything is dorked up.

Specifically I'm running the 2.6.15-21-686, but when I go into Synaptic gui to install the kernel source and kernel headers all I see is the 2.4 kernel.   ???????????????

Same thing when I do it from the command line:

```
jackal@jackal:~$ uname -a
Linux jackal 2.6.15-21-686 #1 SMP PREEMPT Fri Apr 21 16:57:03 UTC 2006 i686 GNU/Linux


jackal@jackal:~$ apt-cache search kernel | grep ^kernel-headers
kernel-headers-2.4.27-2 - Header files related to Linux kernel version 2.4.27
kernel-headers-2.4.27-2-386 - Linux 2.4.27 kernel headers for 386
kernel-headers-2.4.27-2-586tsc - Linux 2.4.27 kernel headers for Pentium-Classickernel-headers-2.4.27-2-686 - Linux 2.4.27 kernel headers for PPro/Celeron/PII/PIII/P4
kernel-headers-2.4.27-2-686-smp - Linux 2.4.27 kernel headers for PPro/Celeron/PII/PIII/P4 SMP
kernel-headers-2.4.27-2-k6 - Linux 2.4.27 kernel headers for AMD K6/K6-II/K6-IIIkernel-headers-2.4.27-2-k7 - Linux 2.4.27 kernel headers for AMD K7
kernel-headers-2.4.27-2-k7-smp - Linux 2.4.27 kernel headers for AMD K7 SMP

```


How do I fix this?  I need the kernel headers for the 2.6.15-21 kernel since that's the kernel I'm running.

---

### Post by kzutter on 2006-05-05
I may be wrong, but I think apt-cache tells about pkgs that have been previously downloaded, not those available from your sources.

I forget apt commands faster than I learn them, but Synaptic has never let me down.

Be sure to hit the "Reload" button in Synaptic so it has the latest list from your sources, then search for kernel pkgs.

If you continue to have problems, we will want to see your sources.list file

---

