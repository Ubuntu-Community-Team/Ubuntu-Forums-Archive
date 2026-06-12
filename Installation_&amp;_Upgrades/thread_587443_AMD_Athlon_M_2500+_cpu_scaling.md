---
title: "AMD Athlon M 2500+ cpu scaling"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by slack31337 on 2007-10-22
I have upgraded to gutsy and noticed my cpu scalin isnt working .. not that i checked on fiesty :) 

anyway i have a AMD Athlon M 2500+ which is the mobile chip in a desktop board and right now it is clocking at 1200+ according to the scaling app. Now stock speed for that proc is 1800+ and i get an error cpuscaling unsupported. I was trying to follow this 

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)

and as i got to "sudo modprobe powernow-k8"

i get this error "FATAL: Error inserting powernow_k8 (/lib/modules/2.6.22-14-generic/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko): No such device"

Anyone have any idea where to go from there?

---

### Post by slack31337 on 2007-10-22
i also tried 

sudo modprobe acpi-cpufreq 

same error

and here is my cpu info

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : Unknown CPU Typ
stepping        : 0
cpu MHz         : 1200.076
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts fid vid
bogomips        : 2402.55
clflush size    : 32

---

### Post by slack31337 on 2008-01-31
so anyone have any ideas i am still unable to figure this out and it is quite annoying

---

### Post by ShamusPatt on 2008-02-19
Check your BIOS settings. I had a similar problem on a Phenom (a newer processor of course). For the Phenom, and an Asus M3A32 board (Award bios), the "Cool 'n Quiet" features have to be enabled in the BIOS. Otherwise some ACPI data doesn't get loaded, and the Powernow-k8 module won't load without it.

This is a bit different situation, because the Phenom is multi-processor (and Powernow-k8 has defaults it applies to single proc systems, apparently). However, there still might be some dependency on BIOS power save settings.

---

