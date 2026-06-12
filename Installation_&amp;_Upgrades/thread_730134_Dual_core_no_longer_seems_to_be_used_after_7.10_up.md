---
title: "Dual core no longer seems to be used after 7.10 upgrade"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by jayach on 2008-03-20
I upgraded to 7.10 from 7.04. 

Unlike some other posts I've seen, like this one:
[http://ubuntuforums.org/showthread.php?t=554370](http://ubuntuforums.org/showthread.php?t=554370)

my Ubuntu is showing both cores, just the kernel doesn't appear to be using both of them anymore like it was in 7.04.  When I'm doing something processor intensive, one core will expectedly max out.  But, when I try to do something else in another app, it will lock up, or work very slowly, all the while, the 2nd core sits idle.  I distinctly remember the same situations in 7.04 not happening because it was my first experience with a dual core cpu:  it was great to see apps work quickly even when another app maxed out another cpu core.  On a rare occasion though, I'll see both cores used.

One thing of interest, when I upgraded, it installed the server kernel in addition to the generic, and defaulted to the server, whereas I only had the generic before.  My network driver didn't work in the server version, so have been using the generic.

Is this my imagination?  What can I look at to troubleshoot?  Thanks in advance.

ls -la /lib/modules/
total 32
drwxr-xr-x  6 root root  4096 2008-02-14 11:14 .
drwxr-xr-x 17 root root 12288 2008-02-28 09:25 ..
drwxr-xr-x  6 root root  4096 2008-02-05 15:50 2.6.20-16-generic
drwxr-xr-x  9 root root  4096 2008-02-14 11:14 2.6.22-14-generic
drwxr-xr-x  5 root root  4096 2008-02-13 09:57 2.6.22-14-server
drwxr-xr-x  3 root root  4096 2008-02-14 11:14 fglrx

uname -r
2.6.22-14-generic

cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz
stepping        : 11
cpu MHz         : 2000.000
cache size      : 4096 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 5988.97
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz
stepping        : 11
cpu MHz         : 2000.000
cache size      : 4096 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 5984.93
clflush size    : 64

---

### Post by Pumalite on 2008-03-20
Post:
uname -a

---

### Post by jayach on 2008-03-20
uname -a
Linux ***************** 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

---

### Post by Pumalite on 2008-03-20
Well, you have the right kernel. I'd be looking at hardware. I doubt that your kernel is not using the resources properly.

---

### Post by jayach on 2008-03-20
Something just doesn't seem right, but hard knowing what with all of the variables.  Upgrading is the only thing I know of that has changed.

Thank you for your time and quick replies.

---

### Post by Pumalite on 2008-03-20
You are welcome. If you can afford an OS in Alpha 6 development, I'd suggest you save your data and take 8.04 Alpha 6 for a spin after a clean install.

---

### Post by jayach on 2008-03-24
This is my work computer I have the dual core issue with, so I'll probably wait a bit.  Stability is more important, although this issue has slowed me down.   I thought I was being safe waiting for 7.10, but ended up wasting nearly an entire day due to issues with the upgrade - mostly ati issues of course.    I am looking forward to the next release though.

---

### Post by Pumalite on 2008-03-24
I have Alpha 6 installed in 2 machines: 32 and 64 bits. Updates up to now are flawless. Minor glitches. Never had to reboot. No loss of data. I have installed Beta in two other machines: 32 and 64 bits. The same results. I things continue this way I'll have Final Releases the 24 of April.

---

