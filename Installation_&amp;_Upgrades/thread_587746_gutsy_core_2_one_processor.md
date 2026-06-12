---
title: "gutsy core 2 one processor"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by honeydew on 2007-10-23
Gutsy only found one of my processors. I have a Intel Core 2 and only 2 were showing under system status.  Is the core 2 reporting in a defferent way to the linux kernel?  in fiesty I remember I always had 2.

---

### Post by ezak on 2007-10-23
If you do indeed have an Intel Core 2 Duo, you will only have 2 cores, not 2 processors. So the answer is yes. Ubuntu Gutsy should, by default, display both processing cores in your system status. Double check just to make sure, that you have the right kernel configured and installed for your processor. :)

---

### Post by finite9 on 2007-10-23
The generic kernel is the only kernel you need for most architectures now.  What is the output of:

```
cat /proc/cpuinfo
```

?

---

### Post by BoardDWorld on 2007-10-23
Just interested to know, the command you posted gave me the following:

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 2048 KB
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
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3662.95
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 2048 KB
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
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3658.88
clflush size    : 64

```

Is this correct considering I have a 1.83GHz CPU? According to the output I am at 2Ghz.

---

### Post by honeydew on 2007-10-23
$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 2
cpu MHz         : 1000.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3329.07
clflush size    : 64

---

### Post by honeydew on 2007-10-23
my uname is..
Linux 2.6.22-14-386 #1 Sun Oct 14 22:36:54 GMT 2007 i686 GNU/Linux

is this because I am running the -386 kernel? maybe Ill try and reinstall the generic kernel...

---

### Post by honeydew on 2007-10-23
hrmm how very strange =].. that did seem to fix things.. the i386 kernel was botching things.. I wonder why..  mmm I guess its time to recompile my drivers =]

---

