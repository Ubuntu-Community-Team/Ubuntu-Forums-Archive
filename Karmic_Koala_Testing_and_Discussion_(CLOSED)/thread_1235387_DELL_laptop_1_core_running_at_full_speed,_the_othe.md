---
title: "DELL laptop: 1 core running at full speed, the other one not"
date: 2009-08-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by danf_1979 on 2009-08-09
Hi guys. One of my cores is running at full speed but the other one is not. /proc/cpuinfo reports one at 1667Mhz, but the second one only at 1000Mhz. I tried $ cpufreq-selector -g performance but it doesn't help. I guess I'm kinda clueless. This is a T2300 Core Duo, on a DELL Inspiron 9400.

Any clues?

/proc/cpuinfo here:
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping	: 8
cpu MHz		: 1667.000
cache size	: 2048 KB
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
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor vmx est tm2 xtpr pdcm
bogomips	: 3327.09
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping	: 8
cpu MHz		: 1000.000
cache size	: 2048 KB
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
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor vmx est tm2 xtpr pdcm
bogomips	: 3324.86
clflush size	: 64
power management:

```

---

### Post by khelben1979 on 2009-08-09
Sometimes software can be buggy. Just because it reports this isn't necessary the truth.

Have you checked inside [BIOS]("http://en.wikipedia.org/wiki/BIOS")?

---

### Post by phenest on 2009-08-09
What does it say it Jaunty, or any other OS?

---

### Post by danf_1979 on 2009-08-09
> **khelben1979 said:**
> Sometimes software can be buggy. Just because it reports this isn't necessary the truth.

Have you checked inside [BIOS]("http://en.wikipedia.org/wiki/BIOS")?

True, but this is the kernel, so I trust it. Anyway, it was true. I managed to get both cores at max frequency (and so does say /proc/cpuinfo) using two cpu-freq applets, one for each core. 

Also, reading cpufreq-selector man (duh):
```

-c NUMBER, --cpu=NUMBER
       number of CPU to set.  If omitted, zeroth CPU is implied.

```

---

### Post by MadMan2k on 2009-08-09
this effect is called powersaving and happens on purpose. if there is nothing to do for the second core, why should it run with full speed?

---

### Post by danf_1979 on 2009-08-09
> **MadMan2k said:**
> this effect is called powersaving and happens on purpose. if there is nothing to do for the second core, why should it run with full speed?

Powersaving happens on battery, and then both cores run at 1000MHz, which is ok. But why would one core run at the lowest possible frequency with the AC adapter?

---

### Post by MadMan2k on 2009-08-09
> **danf_1979 said:**
> Powersaving happens on battery, and then both cores run at 1000MHz, which is ok. But why would one core run at the lowest possible frequency with the AC adapter?
probably there is nothing to do for the second core. see: [http://www.linuxinsight.com/ols2006_the_ondemand_governor.html](http://www.linuxinsight.com/ols2006_the_ondemand_governor.html)

---

