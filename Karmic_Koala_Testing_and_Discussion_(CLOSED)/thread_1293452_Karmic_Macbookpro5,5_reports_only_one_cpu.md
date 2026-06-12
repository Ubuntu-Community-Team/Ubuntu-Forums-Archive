---
title: "Karmic Macbookpro5,5 reports only one cpu"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by shivathreya on 2009-10-17
I installed Karmic beta on my Macbookpro5,5. Everything works except that number of cpu core is shown as 1.

shiva@shiva-laptop:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     P7550  @ 2.26GHz
stepping	: 10
cpu MHz		: 798.000
cache size	: 3072 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 4510.13
clflush size	: 64
power management:

Anybody faced this issue?

Shiva

---

