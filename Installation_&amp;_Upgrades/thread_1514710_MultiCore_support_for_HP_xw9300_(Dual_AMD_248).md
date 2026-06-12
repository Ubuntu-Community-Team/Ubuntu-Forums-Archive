---
title: "MultiCore support for HP xw9300 (Dual AMD 248)"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by NetDesignate on 2010-06-21
I have recently loaded the new LTS SERVER 10.04 release and it loaded without errors.

My only issue is that it does not seem to correctly identify the Dual Cores for each processor. (The HP xw9300 I have has two hardware CPUs - each one being Dual-Core - so there should be a total of 4 CPUs recognized - unless I am mistaken?)

If anyone knows how I can debug the processor recognition for multi-core support to get the additional cores recognized, please let me know...

[B]My /proc/cpuinfo file looks like this:
[/B]
```
xxxx@hostname:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 37
model name      : AMD Opteron(tm) Processor 248
stepping        : 1
cpu MHz         : 2194.452
cache size      : 1024 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow rep_good pni lahf_lm
bogomips        : 4388.90
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 37
model name      : AMD Opteron(tm) Processor 248
stepping        : 1
cpu MHz         : 2194.452
cache size      : 1024 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow rep_good pni lahf_lm
bogomips        : 4388.42
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

```

---

### Post by davidmohammed on 2010-06-21
check you BIOS ACPI settings.  ACPI has to be enabled.  Some BIOS settings don't have ACPI set correctly.

---

