---
title: "64 or 32 bits for my configuration"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by Jemator on 2011-11-14
Hello all,
 
I'm actually running an ubuntu 32 bits version on my machine, but since there is 8Go of RAM on the motherboard, I am thinking to install a 64 bits version.
 
Is this possible on this machine :
 
cpuinfo :
 
processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 23
model name : Intel(R) Xeon(R) CPU X5482 @ 3.20GHz
stepping : 10
cpu MHz : 3191.978
cache size : 6144 KB
physical id : 0
siblings : 4
core id : 0
cpu cores : 4
apicid : 0
initial apicid : 0
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 13
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips : 6383.95
clflush size : 64
cache_alignment : 64
address sizes : 38 bits physical, 48 bits virtual
power management:
processor : 1
vendor_id : GenuineIntel
cpu family : 6
model : 23
model name : Intel(R) Xeon(R) CPU X5482 @ 3.20GHz
stepping : 10
cpu MHz : 3191.978
cache size : 6144 KB
physical id : 0
siblings : 4
core id : 2
cpu cores : 4
apicid : 2
initial apicid : 2
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 13
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips : 6383.96
clflush size : 64
cache_alignment : 64
address sizes : 38 bits physical, 48 bits virtual
power management:
processor : 2
vendor_id : GenuineIntel
cpu family : 6
model : 23
model name : Intel(R) Xeon(R) CPU X5482 @ 3.20GHz
stepping : 10
cpu MHz : 3191.978
cache size : 6144 KB
physical id : 0
siblings : 4
core id : 1
cpu cores : 4
apicid : 1
initial apicid : 1
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 13
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips : 6383.99
clflush size : 64
cache_alignment : 64
address sizes : 38 bits physical, 48 bits virtual
power management:
processor : 3
vendor_id : GenuineIntel
cpu family : 6
model : 23
model name : Intel(R) Xeon(R) CPU X5482 @ 3.20GHz
stepping : 10
cpu MHz : 3191.978
cache size : 6144 KB
physical id : 0
siblings : 4
core id : 3
cpu cores : 4
apicid : 3
initial apicid : 3
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 13
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips : 6383.94
clflush size : 64
cache_alignment : 64
address sizes : 38 bits physical, 48 bits virtual
power management:
 
uname -a :
 
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
 
The following test taken from [http://doc.ubuntu-fr.org/ubuntu_64bits](http://doc.ubuntu-fr.org/ubuntu_64bits) returns "false", but I would like to make sure with you.
 
if [[ $(sed -n '/flags/{/lm/ p;q}' /proc/cpuinfo) ]] ; then echo "Compatible 64 bits" ; else echo "Non-compatible 64 bits" ; fi 
Thank you

---

### Post by fantab on 2011-11-14
Welcome to the Forums!

Firstly, 64bit or 32bit architecture has nothing to do with RAM it is a CPU thing.

YES, with your CPU you Should be using 64bit. So go ahead and install Ubuntu-64bit.

---

### Post by Jemator on 2011-11-14
Thank you, I will install it.
 
I know it is a CPU thing, but with a 32bit architecture aren't you limited in the amount of RAM that the cpu can adress ? For example, there is 8Go of RAM on my motherboard while my Ubuntu 32 bits uses only 3.2Go. That's why I want to upgrade to the 64 bits version.

---

### Post by Topsiho on 2011-11-14
Hello Jemator,

You are quite right in stating that with more than a certain amount of Ram one should install a 64 bits version of the OS: 32 bits doesn't see all Ram if more than 3 or 4 GB (I forgot which) of Ram is installed, which would be a waste.

So go ahead, and try (LiveCD) a 64 bits version, and if everything seems OK, than by all means install it.

What in the past was against 64 bits, was that with 32 bits there was a lot more experience, but with all those 64 bit machines that's not true anymore.

:)

Topsiho

---

### Post by dino99 on 2011-11-14
enable PAE setting into the bios, then install ONLY generic-pae kernel from synaptic, then all your ram will be usable.

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

note: actually Ubuntu propose 32 bits by default, this will be changed when next Precise will be released.

---

