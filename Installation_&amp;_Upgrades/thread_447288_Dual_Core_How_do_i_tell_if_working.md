---
title: "Dual Core? How do i tell if working???"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by storx on 2007-05-17
how do i tell if dual core is working in the OS???

---

### Post by Ziox on 2007-05-17
you can always open up system monitor.  

There should be a separate reading for each of your cores.

---

### Post by sethdotcom on 2007-05-17
I wish i had 2 cores, can u really tell that much of a speed difference?

---

### Post by PilotJLR on 2007-05-17
I think so... Core 2 Duo is WAY faster than a high end P4 or Athlon.

You can also do this:
```

cat /proc/cpuinfo

```

If you see an entry for "processor: 0" and "processor: 1" then the kernel is using both cores.

---

### Post by storx on 2007-05-18
[code]storx@Storx:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-50
stepping        : 2
cpu MHz         : 1607.341
cache size      : 256 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dno
wext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 3231.58
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-50
stepping        : 2
cpu MHz         : 1607.341
cache size      : 256 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov                                                                                                    pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dno                                                                                                   wext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 3230.89
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc[/code/

hows that look?
I looked in system monitor there is only one displayed.

---

### Post by storx on 2007-05-18
doesnt cost much for the dual core setups now adays... i just upgraded my desktop to dual core adn the motorboard and dual core TL-54 processor was under 100.00 on ebay.

---

### Post by PilotJLR on 2007-05-18
Yep, looks good - you're using both cores

---

### Post by Lanky Juggler on 2007-05-18
I definitely am using both by whatever methods are posted above, but the second core rarely gets used more than 3 percent or so.  If i have system moniter on, it'll just load the first processor up to 100% and the second processor will still be hovering around 2-3%.  Is that the way it is supposed to work? I figured they were meant to seperate tasks and work as a team or something.  Also, when looking at Processor Use, it never gets above 53% (well yeah, duh).  I realize I haven't been doing too much heavy stuff with my computer yet, but it seems weird that one processor would do all the work?

---

### Post by quinreis on 2007-05-18
> **storx said:**
> how do i tell if dual core is working in the OS???

Easy. Run " top " from a console. Then hit " 1 ". If multiple CPUs are running, you will get a running report of how hard they are each working.

---

### Post by storx on 2007-05-18
> Easy. Run " top " from a console. Then hit " 1 ". If multiple CPUs are running, you will get a running report of how hard they are each working.

can you explain more about this???

---

### Post by cookfromfrozen on 2007-05-19
> **storx said:**
> can you explain more about this???
Open a terminal and type top.

By default, it shows combined usage for all CPUs, but if you press 1 on the keyboard, it separates them out and shows usage stats for each individual CPU, e.g. CPU0, CPU1 etc.

---

