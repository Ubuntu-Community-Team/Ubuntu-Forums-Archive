---
title: "Processor Frequency Verification?"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by Portent on 2007-10-28
Just installed ubuntu 7.10 today on an Intel E2180 system.  I have the system overclocked, but I'm having trouble verifying that. All I want is some system verification that it's running at whatever GHz I've chosen in the BIOS. 

Below is what I get when I use the cpuinfo command (cat /proc/cpuinfo).  You might be wondering why it says "cpu MHz: 1200.000" if I have a 2.0 GHz E2180 that's overclocked, but that seems to be tied to the ubuntu CPU frequency scaling monitor which is set to "OnDemand".  It just shows whatever I choose the processor to be scaled at, which means that the "cpu MHz" value is not the actual frequency the processor is currently clocked to.  When I choose to scale it at 2.0 GHz (the highest setting in the frequency scaling monitor), the "cpu MHz:" changes to 2.0 GHz, but nothing else changes.

But here's what I'm interested in... the bogomips are the only things to show a changed value after an overclock.  When I change the overclock from 2.3 GHz to 2.6 GHz, the bogomips value goes from about 4600 to about 5200.  So is that a reliable way to verify that my system is overclocked?

If I haven't been clear, here's the bottom line.  If I have my system overclocked to 2.3 GHz, how do I know it's actually running at 2.3 GHz?

This is with the processors at a supposed 2.3 GHz
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
stepping        : 13
cpu MHz         : 1200.000
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4600.42
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
stepping        : 13
cpu MHz         : 1200.000
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4598.73
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:


And THIS is with the processors at a supposed 2.6GHz

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
stepping        : 13
cpu MHz         : 1200.000
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 5200.84
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
stepping        : 13
cpu MHz         : 1200.000
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 5198.99
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

---

### Post by jackocleebrown on 2007-10-28
I am no expert....just a simple idea, add a cpu frequency scaling monitor to the gnome panel - it reads my processor frequency fine even though I am unsupported for scaling.

Jack.

---

### Post by Portent on 2007-10-28
I do have the monitor on my gnome panel already.  All it does is show me what the processor is running at currently and it only goes up to 2.0 GHz.  It's like a speedometer that goes to 155, but I know my car is capable of doing 200.  Does that make sense?  I want something that tells me what my top speed is.

---

### Post by jackocleebrown on 2007-10-28
does this do it for you

"cat /proc/cpuinfo"

---

### Post by Portent on 2007-10-28
No... as I said above, the only useful thing that gives me is bogomips.  But thanks...

---

