---
title: "/proc/cpuinfo wrong, whats going on?"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by varean on 2006-08-27
I have an Athlon64 3500+ thats 2.2 GHz, however, /proc/cpuinfo says otherwise:
```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 39
model name      : AMD Athlon(tm) 64 Processor 3500+
stepping        : 1
cpu MHz         : 1000.108
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips        : 2003.02

```

Any ideas?

---

### Post by hizaguchi on 2006-08-28
No clue why, but I have a similar situation going on.  When using powersaved to scale my processors, the "bogomips" reading changes as expected, but the reported cpu frequencies do not.

---

### Post by MrHorus on 2006-08-28
> **varean said:**
> 

Any ideas?

Is it a laptop?

It could be throttling the CPU if is.

---

### Post by hizaguchi on 2006-08-28
Yeah, mine's a laptop.  But normally (using cpufreqd or powernowd in Arch Linux) when the cpu is being controlled the frequency displays in nice round numbers (1600 or 800 MHz in my case) and scales along with the bogomips.  However in Ubuntu, the bogomips number is behaving as expected, but the cpu frequencies act the way they do when they are not being controlled at all.

---

### Post by varean on 2006-08-28
Its an actual PC, i still have no idea whats going on.

---

