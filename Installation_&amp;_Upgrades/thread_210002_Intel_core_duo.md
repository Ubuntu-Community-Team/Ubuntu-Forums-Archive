---
title: "Intel core duo ???"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by eldher on 2006-07-06
Hello

I have a Dell
 inspiron 6400 with intel core duo.
I check de /proc/cpuinfo and i only have one processor (0)in this file.
what can i do resolve this problem?
I tested this laptop with fedora core 5 and this SO recognized 2 processor (0,1)

/proc/cpuinfo
root@eldher-laptop:~# more /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 997.655
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pni monitor vmx est tm2 xtpr
bogomips        : 1996.74

Thanks a lot.

---

### Post by SIKLS1 on 2006-07-06
If you want to get both CPU cores working, you need to install the SMP (symmetric multi-processing) kernel, you can easily do this installing the linux-686-smp package after the default installation, (the system works as well with one core only) using apt or synaptic.

---

