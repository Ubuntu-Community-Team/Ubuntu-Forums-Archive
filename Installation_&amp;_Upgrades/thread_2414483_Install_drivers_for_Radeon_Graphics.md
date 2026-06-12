---
title: "Install drivers for Radeon Graphics"
date: 2019-03-11
forum: Installation &amp; Upgrades
---

### Post by maramsumanth on 2019-03-11
I want to install AMD Radeon graphics for my ubuntu budgie 18.10. This is my current Graphics **Intel® HD Graphics 620 (Kaby Lake GT2)**
I want to change it to AMD Radeon. How to install appropriate drivers for this ?

I am running dual boot with Windows 10 and ubuntu budgie 18.10. When I open windows, the default graphics is radeon, but when I boot ubuntu, it is taking intel graphics

This is my output for **lscpu** :-
```
Architecture:        x86_64
CPU op-mode(s):      32-bit, 64-bit
Byte Order:          Little Endian
CPU(s):              4
On-line CPU(s) list: 0-3
Thread(s) per core:  2
Core(s) per socket:  2
Socket(s):           1
NUMA node(s):        1
Vendor ID:           GenuineIntel
CPU family:          6
Model:               142
Model name:          Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz
Stepping:            9
CPU MHz:             1592.360
CPU max MHz:         3100.0000
CPU min MHz:         400.0000
BogoMIPS:            5424.00
Virtualization:      VT-x
L1d cache:           32K
L1i cache:           32K
L2 cache:            256K
L3 cache:            3072K
NUMA node0 CPU(s):   0-3
Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp flush_l1d
```

---

### Post by Autodave on 2019-03-11
First of all, you should not need to install anything: Ubuntu comes with the AMDGPU driver(s).  Power down, install card, connect monitor to new card, power up.

If you want or need to install the AMDGPU Pro driver, then this link will tell you how: [URL="https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&cad=rja&uact=8&ved=2ahUKEwjg1bSqrfrgAhXyp1kKHUIuBV4QFjACegQICRAB&url=https%3A%2F%2Fwww.amd.com%2Fen%2Fsupport%2Fkb%2Ffaq%2Fgpu-635&usg=AOvVaw2G_72jU9BNdqDdeU6Qux9G"]https://www.amd.com/en/support/kb/faq/gpu-635
[/URL]
Again, you probably won't need to do anything.

---

