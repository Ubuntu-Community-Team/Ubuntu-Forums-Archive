---
title: "dmesg doesn't contain &quot;processor&quot;-OK?"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2006-11-19
Hi,
I'm on Kubuntu Edgy with an Athlon 64b processor.
I successfully compiled the latest (2.6.18.3) kernel, and, immediately after booting this kernel ran (as root) dmesg. I was amazed that dmsg did NOT refer to the processor( see below) at all. Otherwise, the systems seems OK.

Is this usual?

TIA  8) 

-------copy of msg | grep  (as root)----------
root@miki-desktop:/usr/src/linux# dmesg | grep processor
root@miki-desktop:/usr/src/linux# dmesg | grep Athlon
------------------------------------------------------------

--------copy of my cpuinfo---------
miki@miki-desktop:~$ cd /proc
miki@miki-desktop:/proc$ cat cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 47
model name      : AMD Athlon(tm) 64 Processor 3200+
stepping        : 2
cpu MHz         : 2010.350
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm ts fid vid ttp tm stc
bogomips        : 4021.77

-----------------------------------------------------------

---

### Post by daller on 2006-11-20
Well, normally you would receive output!

[17179569.184000] Detected 1498.979 MHz processor.
[17179571.212000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.292000] CPU: Intel(R) Pentium(R) M processor 1500MHz stepping 05

But since the computer works, and /proc/cpuinfo tells you the correct info (I assume), then you have no problem!

Cheers!

---

### Post by mibadt on 2006-11-22
That's exactly was I was thinking.

Thanks

---

