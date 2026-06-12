---
title: "Pentium D not seen as 2 cores."
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by Aron Schatz on 2007-10-28
Hello all. Ubuntu is great. I'm actually a Kubuntu user (wish that project would get more polishing like regular Ubuntu does...)

Anyway, I'm having a problem on one of my systems. It is a Pentium D 830 on an Intel 955XBK. When I boot with the Kubuntu 7.10 live cd, /proc/cpuinfo shows two cores as it should...

When Kubuntu gets installed, this is what /proc/cpuinfo shows...
```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) D CPU 3.00GHz
stepping        : 4
cpu MHz         : 3000.404
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
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 6005.88
clflush size    : 64
```

Why is the installation different from the Live? My kernel is SMP...

uname -a: Linux aseremote 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

I'm stumped... Both my Core 2 Duo machines work fine??

---

### Post by Aron Schatz on 2007-10-29
Anyone?

---

