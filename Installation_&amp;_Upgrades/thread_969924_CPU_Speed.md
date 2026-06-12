---
title: "CPU Speed"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by fred0843 on 2008-11-03
Have Ubuntu 8.10 installed on a AMD 64 FX 55.When I do a cat /proc/cpuinfo it shows only 1200 Mhz Speed should be 2459 Mhz. Why?

---

### Post by Partyboi2 on 2008-11-03
deleted

---

### Post by Pumalite on 2008-11-03
There are two processors in a Core 2 Duo:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping	: 6
cpu MHz		: 1596.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4800.14
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping	: 6
cpu MHz		: 1596.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4800.18
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

---

### Post by pansz on 2008-11-03
AMD has a cool&quiet technology which will run CPU at a slower frequency when idle. So IMO it is quite normal to see 1.2GHz instead of 2.5GHz. If you run some time-consuming calculations and see cpuinfo whilst the calculation running, you should see 2.5GHz.

---

### Post by fred0843 on 2008-11-03
Ok that may explain why I seen the higher speed then it went back to the lowwer speed. If I disable cool N Quit in the bios will that make a difference ?

---

