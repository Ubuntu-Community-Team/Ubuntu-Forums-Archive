---
title: "Linux 2.6.22 generic kernel not stable on 7.10?"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by newway on 2007-10-29
after auto-upgrade from 7.04 to 7.10, on my dual core AMD, only 1 cpu is detected. After some search
on the intenet, it seems to be the linux-i386-2.6.22 kernel that is causing the problem, after switching
to  linux-generic-2.6.22, 2 cpu now is detected, however, it is not stable on my PC, after sometime it
hangs, and I cannot find anything helpful. when I switch back to i386 kernel it is no problem...

please advice...
thanks.

---

### Post by sistoviejo on 2007-10-31
how do you find out how many cpus were detected?

---

### Post by newway on 2007-10-31
well,  look at the administration -> system monitor

or  more /proc/cpuinfo  to show you.

---

### Post by sistoviejo on 2007-10-31
I don't know why you have this problem.
I have a laptop with Dual AMD Turion 64 (laptop model HP tx1215nr). 
Both CPUs are detected. I am using 7.10 for AMD64.
Hope you find a solution.

more info:

root@silvio-laptop:/# cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-56
stepping        : 2
cpu MHz         : 1800.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips        : 3604.81
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-56
stepping        : 2
cpu MHz         : 1800.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips        : 3604.81
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

root@silvio-laptop:/#

---

