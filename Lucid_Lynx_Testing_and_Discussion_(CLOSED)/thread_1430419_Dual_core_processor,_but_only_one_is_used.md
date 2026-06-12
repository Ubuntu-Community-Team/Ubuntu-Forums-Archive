---
title: "Dual core processor, but only one is used"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by anaconda on 2010-03-15
I have:
AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
and the kernel is
2.6.32-16-generic

But according to /proc/cpuinfo or system monitor
Only one of my cores is being used?!?!?

Does anyone know how to enable the 2nd core?

---

### Post by Owen.C93 on 2010-03-15
Solved?

---

### Post by anaconda on 2010-03-15
No, it isn't solved.
Damn. Maybe I have to start a new thread ?

I know how to mark a thread solved, but there doesn't seem to be a possibility to re-open a solved thread.

Back to the problem:
Maybe I should try with a different kernel? Althought I thought that generic kernel does support dual core processors.

PS. there is a reason why I have to use 32bit ubuntu. 
It is a program, which would be very difficult to get working in 64bit ubuntu. Havn't tried myself, but I know several people (at work), who had to change back to 32bit, when they couldn't get it working with 64bit..

---

### Post by dino99 on 2010-03-15
what do you see into system monitor ?
my quad is fully used here

---

### Post by mcduck on 2010-03-15
> **anaconda said:**
> I have:
AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
and the kernel is
2.6.32-16-generic

But according to /proc/cpuinfo or system monitor
Only one of my cores is being used?!?!?

Does anyone know how to enable the 2nd core?

The generic kernel does support multiple cores/processors.

What do you mean when you say that /proc/cpuinfo says only one core is used? Does it only list one processor or two (note that the numbering starts from 0 so for dual-core you should see cores 0 and 1).

Having a dual-core processor doesn't automatically make all programs use more than one core. If a program only runs in single thread then it can only use one processor/core. And not all tasks can even be broken into multiple threads. So it's absolutely normal if you see a program only using one core, but you definitely should *see* both cores.

edit: Could you post the output of "cat /proc/cpuinfo" here?

---

### Post by cariboo on 2010-03-15
Removed the solved tag. If you need a title changed, report the post, and someone will do it for you.

---

### Post by cariboo on 2010-03-15
Because of this thread, I checked, /proc/cpuinfo only shows one core, and System->Administration->System Monitor only shows one core.

```
cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 75
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping	: 2
cpu MHz		: 2008.958
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips	: 4017.91
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc
```

---

### Post by rtalcott on 2010-03-15
I had this problem...dual core Athlon64 showed two cores with 9.04 but only one with 9.10...same hardware....never did get that one resolved.
rt

---

### Post by Dougie187 on 2010-03-15
My core2 duo also shows up as one core.

EDIT: Nm, I was being dumb.

---

### Post by Alexandre Putt on 2010-03-15
No problem with Pentium(R) Dual-Core CPU T4200 using 10.04 (2.6.32-16),  or previous versions / kernels.

The output you get sounds suspicious.

---

### Post by mcduck on 2010-03-15
That's strange, there must be some bug in the kernel or something. Definitely worth reporting as a bug...

(I'm running 2.6.32-16-generic on a Core Duo T2300, and both cores are recognized correctly.)

---

### Post by cariboo on 2010-03-15
I just checked with todays daily build, only one core gets detected with it too.

**Edit** I just checked my netbook, it has an Atom N270 cpu, it is detected as a dual core due to hyper-threading.

---

### Post by lime4x4 on 2010-03-15
all 4 of my cores show up

john@john-desktop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X4 925 Processor
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 6159.86
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X4 925 Processor
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 6160.49
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 2
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X4 925 Processor
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 6160.49
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 3
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X4 925 Processor
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
apicid		: 3
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 6160.49
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

john@john-desktop:~$

---

### Post by ronacc on 2010-03-15
My amd64X2 4600 shows both cores active see screenshot , cores ,speed and temps all read , note screenlets and pannel , cores are running hard because of boinc .

---

### Post by executorvs on 2010-03-15
I have a tri-core Phenom II 705e and it shows up fine. actually where it hadn't been identifying the processor series or model correctly in earlier ubuntu it does detect it correctly now.

My laptop is a single core Pentium SU2700 but all of the processor specific info is also detected correctly.

Does this seem to be restricted to dual-cores. I noticed the mention of similar behavior on a dual core athlon, I'll try to confirm this on a friend's desktop after class tonight.

I have no access to any other tri or quad core processors, but I might check my old pentium 3 dual processor board as well.

---

### Post by cariboo on 2010-03-15
I have Lucid running on another system, both cores get detected properly:

```
cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 6
model name	: AMD Athlon(tm) II X2 240 Processor
stepping	: 2
cpu MHz		: 2813.236
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 5626.46
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 6
model name	: AMD Athlon(tm) II X2 240 Processor
stepping	: 2
cpu MHz		: 2813.236
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 5626.07
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate
```

It runs the same motherboard as in post #7, just a newer cpu and faster ram.

---

### Post by lidex on 2010-03-15
Another Athlon 64x2 4600 here; both cores working and detected properly. 2.6.32-16 generic kernel. Is it just the 3800?

---

### Post by executorvs on 2010-03-15
for the people with the amd athlon x2 4600 and 3600 how did you move to lucid? was it upgrade or clean install? I'm just wondering if one path might not have configured something correctly. have you also checked the improperly detected board with today's live daily? and are you all running 64bit lucid?

---

### Post by rtalcott on 2010-03-15
The Athlon64 X2 that I had problems with was either a 4200 or 4400...don't have the cpu now so I am not certain...I am currently running 5 AMD boards and only one had the problem with recognizing multiple cores...

rt

---

### Post by lidex on 2010-03-15
> **executorvs said:**
> for the people with the amd athlon x2 4600 and 3600 how did you move to lucid? was it upgrade or clean install? I'm just wondering if one path might not have configured something correctly. have you also checked the improperly detected board with today's live daily? and are you all running 64bit lucid?

64 bit here. Clean install - I'm not adventurous enough to upgrade to an Alpha build. No problem with cpu detection.

---

### Post by cariboo on 2010-03-15
I'm using 64-bit on both AMD powered systems. The system where both cores aren't detected is a clean install from a daily build from March 5Th, but todays daily build, just running the Live CD, makes no difference.

---

### Post by ronacc on 2010-03-15
I originally upgraded from karmic but did a reinstall at A2 due to trying nouveau and screwing up my video , both cores worked both times .

---

### Post by clhsharky on 2010-03-15
HI

Both cores reported here. Lucid 64. fresh install, AMD 4800.

Sharky

---

### Post by JohnJackson on 2010-03-15
Ensure you have ACPI features enabled in your BIOS, I didn't and had the same problem.

---

### Post by ViRMiN on 2010-03-15
All okay for me too - 64-bit clean install

---

### Post by cariboo on 2010-03-15
> **JohnJackson said:**
> Ensure you have ACPI features enabled in your BIOS, I didn't and had the same problem.

Thank you, that solved my problem, in my case we can chalk it up to user error. :)

---

### Post by anaconda on 2010-03-17
Thank you!
Enabling ACPI from BIOS solved my problem also. :)

But the strange thing is, I have a dualboot, and Hardy heron (8.04) detected and detecs both cores no matter if ACPI is enabled or not.

---

