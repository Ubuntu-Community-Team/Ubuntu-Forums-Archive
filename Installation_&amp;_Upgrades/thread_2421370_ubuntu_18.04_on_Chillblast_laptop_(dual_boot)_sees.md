---
title: "ubuntu 18.04 on Chillblast laptop (dual boot) sees only 1 CPU"
date: 2019-06-20
forum: Installation &amp; Upgrades
---

### Post by angelo-mastro on 2019-06-20
Dear Community,
 
I have set up a dual boot on this laptop [here]("https://www.chillblast.com/chillblast-photo-oc-mobile-5-4k-photo-editing-laptop.html?category_id=509"), using this Ubuntu Desktop 18.04 [here]("https://ubuntu.com/download/desktop"). The C:\\ disk (240GB) is taken by Windows 10, and about half the disk D:\\ (1TB) is taken by ubuntu ( "/"=400GB, "Swap"=64GB), and the boot loader is from the windows one.

In the boot loader, I had to set **acpi=off** option in to let ubuntu start, and after installation I saved that option in /etc/defaults/grub then did **sudo update-grub**. This guarantees me the the system starts or switches off when I choose to use Ubuntu instead of Windows.

The computer runs very slow, so I tried to type** nproc**, and it's equal to 1 (should be 12, as it is on windows). Same result with **cat /proc/cpuinfo**
```

$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 158
model name    : Intel(R) Core(TM) i7-8750H CPU @ 2.20GHz
stepping    : 10
microcode    : 0xb4
cpu MHz        : 3900.001
cache size    : 9216 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 22
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d
bugs        : cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass l1tf mds
bogomips    : 4416.00
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:

```

What can I do ?

---

### Post by CatKiller on 2019-06-20
The reason is likely because you've crippled the interface to the hardware by using acpi=off. That is brutal. You've not said why you thought you needed to do that, nor which other things you'd tried first. There are many gentler Grub options that will let you retain the functionality that you've currently decided to turn off.

---

### Post by oldfred on 2019-06-21
Have you updated UEFI, and SSD firmware?

some more info:
[https://askubuntu.com/questions/139157/booting-ubuntu-with-acpi-off-grub-parameter/139174](https://askubuntu.com/questions/139157/booting-ubuntu-with-acpi-off-grub-parameter/139174)
[https://wiki.archlinux.org/index.php/ACPI_modules](https://wiki.archlinux.org/index.php/ACPI_modules)

---

