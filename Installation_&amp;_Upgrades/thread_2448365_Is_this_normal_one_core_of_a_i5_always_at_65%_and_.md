---
title: "Is this normal one core of a i5 always at 65% and kworker always 18-19%"
date: 2020-08-06
forum: Installation &amp; Upgrades
---

### Post by adrian-h on 2020-08-06
I have done a new desktop install of Ubuntu 20.04, this is on an HP6300 small form factor PC.

an output for lscpu gives me:
```
Architecture:                    x86_64
CPU op-mode(s):                  32-bit, 64-bit
Byte Order:                      Little Endian
Address sizes:                   36 bits physical, 48 bits virtual
CPU(s):                          4
On-line CPU(s) list:             0-3
Thread(s) per core:              1
Core(s) per socket:              4
Socket(s):                       1
NUMA node(s):                    1
Vendor ID:                       GenuineIntel
CPU family:                      6
Model:                           58
Model name:                      Intel(R) Core(TM) i5-3470 CPU @ 3.20GHz
Stepping:                        9
CPU MHz:                         3051.738
CPU max MHz:                     3600.0000
CPU min MHz:                     1600.0000
BogoMIPS:                        6385.69
Virtualisation:                  VT-x
L1d cache:                       128 KiB
L1i cache:                       128 KiB
L2 cache:                        1 MiB
L3 cache:                        6 MiB
NUMA node0 CPU(s):               0-3
Vulnerability Itlb multihit:     KVM: Vulnerable
Vulnerability L1tf:              Mitigation; PTE Inversion
Vulnerability Mds:               Mitigation; Clear CPU buffers; SMT disabled
Vulnerability Meltdown:          Mitigation; PTI
Vulnerability Spec store bypass: Mitigation; Speculative Store Bypass disabled v
                                 ia prctl and seccomp
Vulnerability Spectre v1:        Mitigation; usercopy/swapgs barriers and __user
                                  pointer sanitization
Vulnerability Spectre v2:        Mitigation; Full generic retpoline, IBPB condit
                                 ional, IBRS_FW, STIBP disabled, RSB filling
Vulnerability Srbds:             Vulnerable: No microcode
Vulnerability Tsx async abort:   Not affected
Flags:                           fpu vme de pse tsc msr pae mce cx8 apic sep mtr
                                 r pge mca cmov pat pse36 clflush dts acpi mmx f
                                 xsr sse sse2 ss ht tm pbe syscall nx rdtscp lm 
                                 constant_tsc arch_perfmon pebs bts rep_good nop
                                 l xtopology nonstop_tsc cpuid aperfmperf pni pc
                                 lmulqdq dtes64 monitor ds_cpl vmx smx est tm2 s
                                 sse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic p
                                 opcnt tsc_deadline_timer aes xsave avx f16c rdr
                                 and lahf_lm cpuid_fault epb pti ssbd ibrs ibpb 
                                 stibp tpr_shadow vnmi flexpriority ept vpid fsg
                                 sbase smep erms xsaveopt dtherm ida arat pln pt
                                 s md_clear flush_l1d

```

Not sure if the above helps or not, but when I check with the system monitor there is a contact usage of the 1st core of around 65% and Kworker seems to be always the top of the cpu use list although the second part of Kworker can seem to change around but typically it goes between 0:1+kacpid. and 0:1+kicpi-notify.

here is a picture screen grab from top.

Can I ask if this is normal,?  It would seem not to be and how would I fix this or what is the cause?

I have another question which this may not be the correct thread for any problems with ncurses in 20.04 compared to 18.04, so thing I use runs OK in 18 but not 20?

TIA

Adrian

---

### Post by CatKiller on 2020-08-06
I can't see the picture on my phone, but no, that's not "normal."

Kworker means that it's a kernel worker thread, doing hardware access type things, and acpi means that it's motherboard hardware access type things. It seems to me that your UEFI is doing things in a way that the kernel isn't expecting, and it's causing problems.

A UEFI update might help, or there may be a kernel option you could use that would mitigate whatever the problem is. Motherboard implementations are notoriously flaky, with many individual quirks. Those are likely to be made harder to deal with if you're in Legacy mode rather than UEFI mode.

---

### Post by adrian-h on 2020-08-06
Hello CatKiller, not sure on the name it makes you sound like a villain. but I am sure it is to do with linux cat!

Anyway, i was not to sure what to do about your comment saying a UEFI update, I went into the computer setup on boot and yes under boot order UEFI is Ubuntu, so at least that told me it was actually UEFI and not legacy boot up.

I did some digging around and found the Bios was very old at version 2.83 so it has taken me a while to get to the latest version of 3.08 going through an intermediate Bios 2.99.  The latest 3.08 apparently has some new microcode! for the processors?

Anyway after a couple of hours updating, now on checking the system monitor all appears well, the cores are pootling along with only the odd peak at around 7% I guess doing some back ground tasks and me typing.

So thank you for your answer it has help me solve one issue.

Adrian

---

