---
title: "Ubuntu reboots on new intel machine, safe graphics work"
date: 2021-06-09
forum: Installation &amp; Upgrades
---

### Post by welefort on 2021-06-09
[https://askubuntu.com/questions/1344667/booting-ubuntu-20-04-on-intel-cpu-causes-reboot](https://askubuntu.com/questions/1344667/booting-ubuntu-20-04-on-intel-cpu-causes-reboot)

Basically, by can only keep ubuntu running in safe graphics mode.   In normal boot up,  I get the desktop for about 5 seconds,  then it reboots.

---

### Post by MAFoElffen on 2021-06-09
You may have installed from an older ISO image, depending where you went and what you downloaded. To ensure you are up to date with the latest...

Look at my sticky on Graphics Resolution in my signature line below. On the Second post, follow the link "[**Temporalrily Booting Into a TTY Text Console**]("http://ubuntuforums.org/showpost.php?p=11383888&postcount=715")"...

Once it boots into a text console, it will verify or not if you have a stable core system (enough to build the graphics layers onto).

In a TTY Console, update the Apt cache and apply updates:
```

sudo apt update
sudo apt upgrade
sudo shutdown -r now

```
That will upgrade the system to Ubuntu LTS 20.04.1 LTS and Linux Kernel 5.8.x ... Which Linux kernel 5.8.0.55 (current in Main today) has the updated Intel video driver modules that may resolve your troubles.

---

### Post by welefort on 2021-06-09
I downloaded the most recent 20.04 version today from ubuntu.  Running the 5.11.0-18 generic kernal

---

### Post by MAFoElffen on 2021-06-09
> **welefort said:**
> I downloaded the most recent 20.04 version today from ubuntu.  Running the [COLOR=#ff0000]5.11.0-18 generic[/COLOR] kernal
Exactly... See your Kernel version? Just applying the current updates will get you to Kernel version 5.8.0.55, and should get you going again. 

Kernel version 5.11 had problems with it's Intel Graphics module as it related to newer Intel processors. Kernel version 5.8 resolved those issues.

---

### Post by welefort on 2021-06-09
It appears I mis-spoke.  I thought I had 20.04.  But I had 21.04.

I will download the 20.04 version and try that.

---

### Post by MAFoElffen on 2021-06-09
Tell me how it goes... I have some of time on my hands today.

You still may have to upgrade, depending when they assembled the ISO image. The patches from Intel only came downstream in April. But I know the current updates in the Main Repository today are good. So you may still have to apply updates... But we shall see, right?

---

### Post by welefort on 2021-06-09
So...got. 20.04 installed. Default settings. Let it sit for 10 min.  No issue.

Sudu apt update. Processed ok.188 updates.

Sudo apt upgrade....rebooted just after downloads...maybe 2-3 packages installed

Powered off, back on. And gui is all sorts of fouled up.  Cant use mouse or kb.  Screen is dark blue,  I only see my documents icon.

Ran recovery mode,  I was able to boot into low graphics mode and repair dpkg( Sudo dpkg --configure -a)

[http://imgur.com/a/j7kRQUm](http://imgur.com/a/j7kRQUm)

Rebooted into normal startup.....boot loop again.

---

### Post by MAFoElffen on 2021-06-09
Dang.... LOL

So was fine on initial install until "after" the first update this time?

---

### Post by welefort on 2021-06-09
Yup.... So I gave up.   Something about the integrated intel graphics is not working.

I have an old nvidia gt630. From the previous build.  Popped it in,  started right up, dual screens high resolution.

I leave that in for now.  Maybe in a year or two I'll try intel again.

---

### Post by MAFoElffen on 2021-06-09
What Processor are you using?
```

sudo cat /proc/cpuinfo
sudo lscpu

```

---

### Post by MAFoElffen on 2021-06-09
Mine also works great with NVidia GTX1660 Ti's.

Sorry to hear that. Dang.

---

### Post by welefort on 2021-06-09
> **MAFoElffen said:**
> What Processor are you using?
```

sudo cat /proc/cpuinfo
sudo lscpu

```


```
$ sudo cat /proc/cpuinfoprocessor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 165
model name    : Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz
stepping    : 5
microcode    : 0xec
cpu MHz        : 3992.517
cache size    : 12288 KB
physical id    : 0
siblings    : 12
core id        : 0
cpu cores    : 6
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 22
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp pku ospke md_clear flush_l1d arch_capabilities
bugs        : spectre_v1 spectre_v2 spec_store_bypass swapgs itlb_multihit
bogomips    : 8199.79
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:


processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 165
model name    : Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz
stepping    : 5
microcode    : 0xec
cpu MHz        : 4255.526
cache size    : 12288 KB
physical id    : 0
siblings    : 12
core id        : 1
cpu cores    : 6
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 22
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp pku ospke md_clear flush_l1d arch_capabilities
bugs        : spectre_v1 spectre_v2 spec_store_bypass swapgs itlb_multihit
bogomips    : 8199.79
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:


processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 165
model name    : Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz
stepping    : 5
microcode    : 0xec
cpu MHz        : 4009.668
cache size    : 12288 KB
physical id    : 0
siblings    : 12
core id        : 2
cpu cores    : 6
apicid        : 4
initial apicid    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 22
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp pku ospke md_clear flush_l1d arch_capabilities
bugs        : spectre_v1 spectre_v2 spec_store_bypass swapgs itlb_multihit
bogomips    : 8199.79
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:


processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 165
model name    : Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz
stepping    : 5
microcode    : 0xec
cpu MHz        : 4100.821
cache size    : 12288 KB
physical id    : 0
siblings    : 12
core id        : 3
cpu cores    : 6
apicid        : 6
initial apicid    : 6
fpu        : yes
fpu_exception    : yes
cpuid level    : 22
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp pku ospke md_clear flush_l1d arch_capabilities
bugs        : spectre_v1 spectre_v2 spec_store_bypass swapgs itlb_multihit
bogomips    : 8199.79
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:


processor    : 4
vendor_id    : GenuineIntel
cpu family    : 6
model        : 165
model name    : Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz
stepping    : 5
microcode    : 0xec
cpu MHz        : 4246.191
cache size    : 12288 KB
physical id    : 0
siblings    : 12
core id        : 4
cpu cores    : 6
apicid        : 8
initial apicid    : 8
fpu        : yes
fpu_exception    : yes
cpuid level    : 22
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp pku ospke md_clear flush_l1d arch_capabilities
bugs        : spectre_v1 spectre_v2 spec_store_bypass swapgs itlb_multihit
bogomips    : 8199.79
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:


processor    : 5
vendor_id    : GenuineIntel
cpu family    : 6
model        : 165
model name    : Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz
stepping    : 5
microcode    : 0xec
cpu MHz        : 4021.821
cache size    : 12288 KB
physical id    : 0
siblings    : 12
core id        : 5
cpu cores    : 6
apicid        : 10
initial apicid    : 10
fpu        : yes
fpu_exception    : yes
cpuid level    : 22
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp pku ospke md_clear flush_l1d arch_capabilities
bugs        : spectre_v1 spectre_v2 spec_store_bypass swapgs itlb_multihit
bogomips    : 8199.79
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:


processor    : 6
vendor_id    : GenuineIntel
cpu family    : 6
model        : 165
model name    : Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz
stepping    : 5
microcode    : 0xec
cpu MHz        : 3980.047
cache size    : 12288 KB
physical id    : 0
siblings    : 12
core id        : 0
cpu cores    : 6
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 22
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp pku ospke md_clear flush_l1d arch_capabilities
bugs        : spectre_v1 spectre_v2 spec_store_bypass swapgs itlb_multihit
bogomips    : 8199.79
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:


processor    : 7
vendor_id    : GenuineIntel
cpu family    : 6
model        : 165
model name    : Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz
stepping    : 5
microcode    : 0xec
cpu MHz        : 3880.059
cache size    : 12288 KB
physical id    : 0
siblings    : 12
core id        : 1
cpu cores    : 6
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 22
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp pku ospke md_clear flush_l1d arch_capabilities
bugs        : spectre_v1 spectre_v2 spec_store_bypass swapgs itlb_multihit
bogomips    : 8199.79
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:


processor    : 8
vendor_id    : GenuineIntel
cpu family    : 6
model        : 165
model name    : Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz
stepping    : 5
microcode    : 0xec
cpu MHz        : 4115.607
cache size    : 12288 KB
physical id    : 0
siblings    : 12
core id        : 2
cpu cores    : 6
apicid        : 5
initial apicid    : 5
fpu        : yes
fpu_exception    : yes
cpuid level    : 22
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp pku ospke md_clear flush_l1d arch_capabilities
bugs        : spectre_v1 spectre_v2 spec_store_bypass swapgs itlb_multihit
bogomips    : 8199.79
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:


processor    : 9
vendor_id    : GenuineIntel
cpu family    : 6
model        : 165
model name    : Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz
stepping    : 5
microcode    : 0xec
cpu MHz        : 4293.317
cache size    : 12288 KB
physical id    : 0
siblings    : 12
core id        : 3
cpu cores    : 6
apicid        : 7
initial apicid    : 7
fpu        : yes
fpu_exception    : yes
cpuid level    : 22
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp pku ospke md_clear flush_l1d arch_capabilities
bugs        : spectre_v1 spectre_v2 spec_store_bypass swapgs itlb_multihit
bogomips    : 8199.79
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:


processor    : 10
vendor_id    : GenuineIntel
cpu family    : 6
model        : 165
model name    : Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz
stepping    : 5
microcode    : 0xec
cpu MHz        : 3938.927
cache size    : 12288 KB
physical id    : 0
siblings    : 12
core id        : 4
cpu cores    : 6
apicid        : 9
initial apicid    : 9
fpu        : yes
fpu_exception    : yes
cpuid level    : 22
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp pku ospke md_clear flush_l1d arch_capabilities
bugs        : spectre_v1 spectre_v2 spec_store_bypass swapgs itlb_multihit
bogomips    : 8199.79
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:


processor    : 11
vendor_id    : GenuineIntel
cpu family    : 6
model        : 165
model name    : Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz
stepping    : 5
microcode    : 0xec
cpu MHz        : 3664.126
cache size    : 12288 KB
physical id    : 0
siblings    : 12
core id        : 5
cpu cores    : 6
apicid        : 11
initial apicid    : 11
fpu        : yes
fpu_exception    : yes
cpuid level    : 22
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp pku ospke md_clear flush_l1d arch_capabilities
bugs        : spectre_v1 spectre_v2 spec_store_bypass swapgs itlb_multihit
bogomips    : 8199.79
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:


midnight@Bootes:~$ sudo lscpu
Architecture:                    x86_64
CPU op-mode(s):                  32-bit, 64-bit
Byte Order:                      Little Endian
Address sizes:                   39 bits physical, 48 bits virtual
CPU(s):                          12
On-line CPU(s) list:             0-11
Thread(s) per core:              2
Core(s) per socket:              6
Socket(s):                       1
NUMA node(s):                    1
Vendor ID:                       GenuineIntel
CPU family:                      6
Model:                           165
Model name:                      Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz
Stepping:                        5
CPU MHz:                         4582.498
CPU max MHz:                     4800.0000
CPU min MHz:                     800.0000
BogoMIPS:                        8199.79
L1d cache:                       192 KiB
L1i cache:                       192 KiB
L2 cache:                        1.5 MiB
L3 cache:                        12 MiB
NUMA node0 CPU(s):               0-11
Vulnerability Itlb multihit:     KVM: Mitigation: VMX unsupported
Vulnerability L1tf:              Not affected
Vulnerability Mds:               Not affected
Vulnerability Meltdown:          Not affected
Vulnerability Spec store bypass: Mitigation; Speculative Store Bypass disabled via prctl and seccomp
Vulnerability Spectre v1:        Mitigation; usercopy/swapgs barriers and __user pointer sanitization
Vulnerability Spectre v2:        Mitigation; Enhanced IBRS, IBPB conditional, RSB filling
Vulnerability Srbds:             Not affected
Vulnerability Tsx async abort:   Not affected
Flags:                           fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss h
                                 t tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_ts
                                 c cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 ss
                                 e4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb
                                  invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rds
                                 eed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_
                                 window hwp_epp pku ospke md_clear flush_l1d arch_capabilities



```

---

### Post by MAFoElffen on 2021-06-09
So integrated is Intel UHD Graphics 630...

Interrupt the Grub Menu boot, and try to edit the boot line to add "nomodeset" to the boot line... and continue the boot. 

<Instructions for that are halfway down post #1 of that same sticky, mine...>

If it does boot with that, then try to boot it by inserting "i915.aplha_support=1" the the boot line and continue the boot.

If that last one works... then add that to your the /etc/default/grub so that it says:
```

GRUB_CMDLINE_LINUX_DEFAULT="i915.alpha_support=1"

```
Then update your grub menu via
```

sudo update-grub

```

---

### Post by welefort on 2021-06-10
If I add nomodeset,  it still reboots a few seconds after the GUI loads.  IF I add i915 alpha line,  it does load,  but at a low (1024x768) resolution,  but it is stable.

This is from 
```
-Display-
Resolution        : 1024x768 pixels
Vendor        : The X.Org Foundation
Version        : 1.20.9
Current Display Name        : :0
-Monitors-
Monitor 0        : 1024x768 pixels
-OpenGL-
Vendor        : Mesa/X.org
Renderer        : llvmpipe (LLVM 11.0.0, 256 bits)
Version        : 3.1 Mesa 20.2.6
Direct Rendering        : Yes
-Extensions-
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
Present
RANDR
RECORD
RENDER
SECURITY
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
default screen number:    0



```


```
lshw -c videoWARNING: you should run this program as super-user.
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:a0000000-a0ffffff memory:90000000-9fffffff ioport:4000(size=64) memory:c0000-dffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.



```

---

### Post by MAFoElffen on 2021-06-10
I'm researching this a bit to come back to you with some kind of qualitive word. Going through Bug report from Kernel.org, X.org. FreeDesktop, Etc. Please bear with me.

---

### Post by MAFoElffen on 2021-06-11
Read through 6 months of Bug Reports on Launch pad, FreeDesktop, Xorg... In the upstream direction. Then I went through parallel reports in the RHEL branch and Debian Branch. Then I went western through other avenues such as Reddit and Tom's Hardware.

Here is what I found out. First, is that it has been hit and miss with Intel UHD and Xe Graphics as it relates to Linux Intel Vidoe Driver Modules, which is nuts, becasue they come down as OpenSourc code, Straight from "from Intel." The problem started out where if you didn't add one of the two boot options that I gave you previously, that the DVI (HDMI) ports were completely turned off! FreeDesktop and Intel worked through that. Unfortunately, using one of those two boot options also cripples it and set it into low resolution.

They went through 5 iterations of patches to try to correct it. About 3 months ago, they got the right combination of patches and put them into the channel to go downstream. 

So then we get to the Linux Branches... In the Debian Branch, the word and fix is updating to Linux Kernel 5.8. That kernel contains all those patches. You have that now... But "your hardware" is still "broken."

Parallel to that (and additionally), there were some board manufacturers that used certain chipsets, that also caused problems using these Processor with Intel Integrated Graphics. So if your had one of those motherboards, then upgrading the kernel (alone), doesn't necessarily make it work. But supposedly, those motherboards came up with firmware and Bios upgrades to correct that. For example, the "ASRock Z370"...

**What motherboard do you have, and is there a firmware upgrade for it?**

---

