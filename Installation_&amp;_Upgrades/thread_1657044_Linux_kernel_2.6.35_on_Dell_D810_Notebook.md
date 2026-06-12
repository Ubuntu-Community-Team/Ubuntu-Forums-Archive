---
title: "Linux kernel 2.6.35 on Dell D810 Notebook"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by icarey on 2010-12-31
Hello,
I am using a Dell D810 Notebook and Ubuntu 10.04 LTS with all the latest upgrades, I would like to know if it is ok to upgrade to Ubuntu 10.10. I have read the release notes and I am not certain if Linux kernel 2.6.35 supports my Notebook. Below I have included out put for cat /proc/cpuinfo and x86info -a

$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 13
model name    : Intel(R) Pentium(R) M processor 2.13GHz
stepping    : 8
cpu MHz        : 800.000
cache size    : 2048 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2
bogomips    : 1596.41
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 32 bits virtual
power management:

////////////////////////////

x86info -a 
x86info v1.25.  Dave Jones 2001-2009
Feedback to <davej@redhat.com>.

Need to be root to use specified options.
Found 1 CPU
--------------------------------------------------------------------------
EFamily: 0 EModel: 0 Family: 6 Model: 13 Stepping: 8
CPU Model: Pentium M (Dothan) [C-0]
Processor name string: Intel(R) Pentium(R) M processor 2.13GHz
Type: 0 (Original OEM)    Brand: 6 (Mobile Intel® Pentium® III processor)
/dev/cpu/0/msr: No such file or directory
Number of cores per physical package=1
Number of logical processors per socket=1
Number of logical processors per core=1
APIC ID: 0x0    Package: 0  Core: 0   SMT ID 0
eax in: 0x00000000, eax = 00000002 ebx = 756e6547 ecx = 6c65746e edx = 49656e69
eax in: 0x00000001, eax = 000006d8 ebx = 00000816 ecx = 00000180 edx = afe9fbff
eax in: 0x00000002, eax = 02b3b001 ebx = 000000f0 ecx = 00000000 edx = 2c04307d

eax in: 0x80000000, eax = 80000008 ebx = 00000000 ecx = 00000000 edx = 00000000
eax in: 0x80000001, eax = 00000000 ebx = 00000000 ecx = 00000000 edx = 00100000
eax in: 0x80000002, eax = 20202020 ebx = 20202020 ecx = 65746e49 edx = 2952286c
eax in: 0x80000003, eax = 6e655020 ebx = 6d756974 ecx = 20295228 edx = 7270204d
eax in: 0x80000004, eax = 7365636f ebx = 20726f73 ecx = 33312e32 edx = 007a4847
eax in: 0x80000005, eax = 00000000 ebx = 00000000 ecx = 00000000 edx = 00000000
eax in: 0x80000006, eax = 00000000 ebx = 00000000 ecx = 08006040 edx = 00000000
eax in: 0x80000007, eax = 00000000 ebx = 00000000 ecx = 00000000 edx = 00000000
eax in: 0x80000008, eax = 00002020 ebx = 00000000 ecx = 00000000 edx = 00000000

Cache info
 L1 Instruction cache: 32KB, 8-way associative. 64 byte line size.
 L1 Data cache: 32KB, 8-way associative. 64 byte line size.
 L2 cache: 2MB, 8-way associative. 64 byte line size.
TLB info
 Instruction TLB: 4K pages, 4-way associative, 128 entries.
 Instruction TLB: 4MB pages, fully associative, 2 entries
 Data TLB: 4K pages, 4-way associative, 128 entries.
 Data TLB: 4MB pages, 4-way associative, 8 entries
 64 byte prefetching.
Feature flags:
 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflsh ds acpi mmx fxsr sse sse2 ss tm pbe
Extended feature flags:
 est tm2

Connector type: Micro-FCBGA

2.10GHz processor (estimate).

////////////////////

Ubuntu 10.04 works very well on my Dell D810
Thank you for your assistance,
Ivan

---

### Post by Idefix82 on 2011-01-01
I would recommend you to burn 10.10 on a CD and try it in a live session first. That's the only way to be sure.

Also, if you have a separate /home partition (so that you can keep all your data) I would always prefer a clean install to an upgrade.

---

