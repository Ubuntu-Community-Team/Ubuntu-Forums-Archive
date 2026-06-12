---
title: "No kernel SMP 686 after Edy upgrade???"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by mcglnx on 2006-12-19
Dear All,

After upgrading to Edgy, I've noticed that the kernel is 386.
I want to use the SMP 686, I tried to uninstall the 386 kernel, re-install the 686. But it seems the default is a 'Generic' and this one seems to be linked with 386.

Any ideas?
How to force the kernel to be 686?

Thanks,
M

---

### Post by kwaanens on 2006-12-19
Use the generic one, it's the one you want.

- Ketil

---

### Post by mcglnx on 2006-12-19
How can I set up the generic one as default?
Thanks.

---

### Post by kwaanens on 2006-12-19
Remove the standard one, and/or edit /boot/grub/menu.lst

- Ketil

---

### Post by mcglnx on 2006-12-20
Thanks! Cheers

---

### Post by sabrewolf2006 on 2006-12-21
Hi,
In regard to this, I am also running a dual core system but seem to have only one active core. (I'm just looking the output of cat /proc/cpuinfo)
I'm running the 2.6.17-10-386 - although the kernel packages installed are linux-image-generic and linux-image-686 (which synaptic says is obsoleted by linux-image-generic).
When I was running Dapper both cores would be listed and each cores load would display in gnome-system-monitor as CPU0 and CPU1 - but just listed as CPU in Edgy.
Are there any kernel arguments at boot-time in order to get the second core running.

Output of cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Pentium(R) D CPU 3.40GHz
stepping        : 4
cpu MHz         : 3401.286
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc up pni monitor ds_cpl est cid cx16 xtpr lahf_lm
bogomips        : 6806.87

Note: This is a 64-bit processor.. I'm just using 32-bit 'cuz I didn't have a 64-bit install disc.

---

### Post by jmmkaiser on 2006-12-21
Hello I have quite the same problem,
My second processor isn't working...
I have a Inspiron 6000 and also the kernel 2.6.17 (Ubuntu Edge efty 6.10)
I have also tried to install the linux-image-686 and linux-restricted-modules-686, but the output of the cat /proc /cpuinfo is still the same...
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.60GHz
stepping        : 8
cpu MHz         : 800.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yesprocessor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.60GHz
stepping        : 8
cpu MHz         : 800.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up est tm2
bogomips        : 1598.45

cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up est tm2
bogomips        : 1598.45

I hope someone can help me...
greetings jmmkaiser

---

