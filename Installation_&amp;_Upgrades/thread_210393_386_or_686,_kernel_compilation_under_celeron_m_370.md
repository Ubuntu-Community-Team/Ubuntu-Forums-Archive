---
title: "386 or 686, kernel compilation under celeron m 370"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by acojlo on 2006-07-06
Hi everyone - I've installed (k)ubuntu a week ago. Just few times a booted second OS (yeah, now I call it second) for some dependant things.

I've compiled newest stable kernel from kernel.org and have a question. My cpu is celeron m 370 (/proc/cpuinfo):
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Celeron(R) M processor         1.50GHz
stepping        : 8
cpu MHz         : 1507.895
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge
                mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm
                pbe up
bogomips        : 3017.75

```
So, should I select "Pentium M" or "Pentium Pro" inside of kernel config cpu?

Also, with gcc is it ok to put gcc optimizations tags inside of ~/.bashrc ? I mean: is bash default for konsole and other possibilites? Like this:

```
export CHOST="i686-pc-linux-gnu"
export CFLAGS="-O2 -march=pentium-m -pipe -fomit-frame-pointer" &&
CXXFLAGS=$CFLAGS

```

---

