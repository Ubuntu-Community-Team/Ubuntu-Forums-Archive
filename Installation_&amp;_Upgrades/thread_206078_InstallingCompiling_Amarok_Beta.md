---
title: "Installing/Compiling Amarok Beta"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by malegria on 2006-06-29
```
checking if C++ programs can be compiled... no
```

That is the error I keep getting after running ./configure in the source of the newest Amarok beta. I have every libstdc++*-dev package installed, and this problem recurs. Could it be because I have a custom built kernel? It's a 2.6.17. 
Here's my /etc/environment
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_US.UTF-8"
LANGUAGE="en"
CHOST="i686-pc-linux-gnu"
CFLAGS="-march=prescott -O2 -pipe -fomit-frame-pointer"
CXXFLAGS="${CFLAGS}"
MAKEOPTS="-j3"
```

I own a PentiumD. Here's my /proc/cpuinfo
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) D CPU 2.80GHz
stepping        : 7
cpu MHz         : 2793.507
cache size      : 1024 KB
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
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips        : 5590.07

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) D CPU 2.80GHz
stepping        : 7
cpu MHz         : 2793.507
cache size      : 1024 KB
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
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips        : 5586.12
```

Any pointers appreciated. Thanks.

---

### Post by bluevoodoo1 on 2006-06-29
Do you have the build-essential package?

---

### Post by malegria on 2006-06-29
Yes I do.

---

