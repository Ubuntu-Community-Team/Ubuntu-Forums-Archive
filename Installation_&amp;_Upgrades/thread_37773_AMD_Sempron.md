---
title: "AMD Sempron"
date: 2005-05-28
forum: Installation &amp; Upgrades
---

### Post by saltydog on 2005-05-28
Investigating why my PC fan was running always too fast, I discovered that my Hoary server (CPU AMD Sempron) is not running powernowd.

this is dmesg output

powernow-k8: Processor cpuid 681 not supported

and this is cat /proc/cpuinfo:

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 8
model name      : AMD Sempron(tm)   2400+
stepping        : 1
cpu MHz         : 1666.642
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse pni syscall mp mmxext 3dnowext 3dnow
bogomips        : 3301.37

Sempron should be supported by powernowd, but it seems powenowd doesn't correctly detect!!  I need some suggestion, before burning my CPU!

---

