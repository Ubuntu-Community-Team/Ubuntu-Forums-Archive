---
title: "32 bit vs 64 bit, again"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by Ampi on 2009-11-22
I know this topic has been posted often, but somehow I still don´t get convinced by any. Or better, I simply don't understand.

I have always had a 32 bit install because I didn't even know there was more. I have a new computer (so I think it is 64 bit, see \proc\cpuinfo below) and I'm going to give it a clean install to get rid of Windows entirely. 

My question now is, what is better, 32 bit or 64 bit??

I would of course like to be able to have my usual software. I don't play games or use and any heavy special software. 
In this topic I really am a dummy.. :)


```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Athlon(tm) 7750 Dual-Core Processor
stepping	: 3
cpu MHz		: 1350.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 5412.10
clflush size	: 64
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Athlon(tm) 7750 Dual-Core Processor
stepping	: 3
cpu MHz		: 1350.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 5411.47
clflush size	: 64
power management: ts ttp tm stc 100mhzsteps hwpstate
```

---

### Post by MelDJ on 2009-11-22
see: [http://en.wikipedia.org/wiki/64_bit](http://en.wikipedia.org/wiki/64_bit)

---

### Post by Ampi on 2009-11-22
Thanks.

Though I guess for me it's useless, because I have only 2GB of RAM plus I'd like to use Skype, this seems to be a possible problem..

[Please Read First Advantages and Disadvantages of 64bit]("http://ubuntuforums.org/showthread.php?t=368607")

Can it be true that my AMD64 Athlon X2 is 64 bit but my motherboard is a 32 bit ???
Wouldn't that be strange?

```
description: Desktop Computer
    product: GA-MA78GM-UD2H
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=30303234-3144-3237-3041-3539FFFFFFFF
```

---

### Post by dhavalbbhatt on 2009-11-22
I don't believe your MB is 32-bit (by that what I mean is, I am sure it will support more than 2GB RAM - it seems like a newer MB to me). With that being said, I have been using a 64 bit Ubuntu OS since 8.10 and it has worked like a charm for me. I am sure you can bump up the RAM on your machine and take advantage of 64 bit computing. Of course, you would be the best person to decide whether you really need 64 bit computing power - is there anything you do which is really processing power / RAM intensive? If so, by all means, go ahead and install a 64 bit OS (you could dual boot with a 32 bit and a 64 bit system). Ubuntu has come a long way in supporting 64 bit applications.

---

### Post by Ampi on 2009-11-22
Oh, I know my MB can support more than 2GB, I only put 2GB in it, it is indeed very new. 
I just saw "32 bits" in its description.
At this point I don't need more than 2GB, the idea is putting in mre within 5 years when I probably will need it. 

Concerning 64-bit, it seems that some software doesn't support it, like Skype for example. That wouldn't work for me...

---

### Post by neerajadsul on 2009-11-22
64 bit processors are useful when you are using applications where large data structures are used. That doesn't have to be limited to only RAM. Because RAM and Swap space both are facilitated by 64 bit. If you are familiar with C - in 32-bit processors, double datatype was bytes wide (4x8=32 bit). Now with the widespread availability of 64-bit processors now the datatype can be 64 bit wide. Therefore you can store even larger numbers and better pecision with floating point.

About applications, yes you are right that some of the applications still doesn't work out of the box for 64 bit installations. (personal experience)

In summary, if you are one working of the following tasks then 64-bit linux would be useful to you. Or else if I were you, I will stick to 32 bit for sometime.
1. Image/Video processing (C/C++/Matlab with 64 bit datatypes support)
2. Other numerical computing where you have really large numbers to process or needs best floating point precision (more than 32-bit)
3. Large files on the disk (e.g. > 3 GB)

---

### Post by Ampi on 2009-11-22
I do use Mathematica every once in a while, but enough to actually use 64 bit I think, and those files, well a movie every once in a while being 4 gb, but no, I don't think it is useful enough for me now to complicate matters.
Thanks for the explanation!

---

