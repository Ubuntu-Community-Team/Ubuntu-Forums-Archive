---
title: "k7 smp with AMD64 X2"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by teepark on 2006-10-09
I have an AMD64 X2 4800, but I want to stick with 32-bit ubuntu for now. As far as I can tell, I have the right kernel packages installed for utilization of both cores, but only one core is being used, and in fact the processor model isn't even being detected completely.
```

teepark@desktop:~$ uname -a
Linux desktop 2.6.15-27-k7 #1 SMP PREEMPT Sat Sep 16 02:35:20 UTC 2006 i686 GNU/Linux
teepark@desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Hammer Family processor - Model Unknown
stepping        : 2
cpu MHz         : 2412.595
cache size      : 1024 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips        : 4830.02
```

I see SMP in the kernel description, and have read in forums that the k7 kernel should provide 32-bit smp for k8 chips, but somehow my cpuinfo doesn't pick up the second core, or even that it's a 4800.

Thanks in advance for any help.

---

### Post by angkor on 2006-10-09
Strange. The k7 kernel should pick up both cores on that proc. It does with my amd dual core processor. What does you bios say about your processor? Some motherboards need a new bios version to support dual core procs.

```
 uname -a
Linux bayon 2.6.15-27-k7 #1 SMP PREEMPT Sat Sep 16 02:35:20 UTC 2006 i686 GNU/Linux
```

```
cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2200.372
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 cl
flush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_lega
cy
bogomips        : 2202.65

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2200.372
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 cl
flush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_lega
cy
bogomips        : 2202.65
```

---

### Post by teepark on 2006-10-24
Bingo. My BIOS also calls it "AMD Hammer Family processor - Model Unknown". Ubuntu is detecting just fine, my BIOS needs an update. Asus's website says that my mobo should support my proc, but not since the earliest drivers for this board, and I've never done a BIOS upgrade. I've looked around a little bit, and I wonder if there is any way to do a BIOS upgrade on an ASUS A8N-SLI if I don't have a floppy drive?

---

### Post by flapane on 2006-10-25
> **angkor said:**
> Strange. The k7 kernel should pick up both cores on that proc. It does with my amd dual core processor. What does you bios say about your processor? Some motherboards need a new bios version to support dual core procs.

```
 uname -a
Linux bayon 2.6.15-27-k7 #1 SMP PREEMPT Sat Sep 16 02:35:20 UTC 2006 i686 GNU/Linux
```

```
cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2200.372
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 cl
flush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_lega
cy
bogomips        : 2202.65

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2200.372
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 cl
flush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_lega
cy
bogomips        : 2202.65
```


I have problems with the 64bit distro, can I use a k7-smp kernel or I could have problems as my x2 3800 is a k8 on a 64bit OS?

---

### Post by Coelocanth on 2006-10-25
> **teepark said:**
> Bingo. My BIOS also calls it "AMD Hammer Family processor - Model Unknown". Ubuntu is detecting just fine, my BIOS needs an update. Asus's website says that my mobo should support my proc, but not since the earliest drivers for this board, and I've never done a BIOS upgrade. I've looked around a little bit, and I wonder if there is any way to do a BIOS upgrade on an ASUS A8N-SLI if I don't have a floppy drive?

I have the same board, and was thinking of dropping a dual core processor into it (I currently have the Athlon 64 3200+ chip). What's your current BIOS version?

If memory serves, you can update the BIOS on-line, although it's only available for Windows, I think. I'll check...

Okay, only in Windows, from what I understand. If you're dual-booting, you can do it. You need to use your support CD that came with your mobo and install the ASUS Update utility. Then you can update over the internet, using that utility.

Other than that, I don't know. Perhaps someone else will have a more elegant solution. Good luck.

---

