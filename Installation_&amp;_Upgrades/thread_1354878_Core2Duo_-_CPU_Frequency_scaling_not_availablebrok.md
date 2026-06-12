---
title: "Core2Duo - CPU Frequency scaling not available/broken?"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by dandanio on 2009-12-14
Guys,

I have been with Ubuntu for years now, recently installed my shiny new Karmic desktop workstation.
For the life of me I can't get the frequency scaling to work.

[FONT=Courier New]root@storm:~# cat /proc/cpuinfo 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping    : 6
cpu MHz        : 2394.201
cache size    : 4096 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips    : 4788.40
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping    : 6
cpu MHz        : 2394.201
cache size    : 4096 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips    : 4788.03
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:[/FONT]

[FONT=Courier New]root@storm:~# modprobe acpi-cpufreq
FATAL: Module acpi_cpufreq not found.[/FONT]
(what happened to this module?)

[FONT=Courier New]root@storm:~# modprobe p4-clockmod 
root@storm:~# cpufreq-info 
cpufrequtils 005: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 300 MHz - 2.40 GHz
  available frequency steps: 300 MHz, 600 MHz, 900 MHz, 1.20 GHz, 1.50 GHz, 1.80 GHz, 2.10 GHz, 2.40 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 300 MHz and 2.40 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.40 GHz (asserted by call to hardware).
  cpufreq stats: 300 MHz:0.00%, 600 MHz:0.00%, 900 MHz:0.00%, 1.20 GHz:0.00%, 1.50 GHz:0.00%, 1.80 GHz:0.00%, 2.10 GHz:0.00%, 2.40 GHz:100.00%
analyzing CPU 1:
  driver: p4-clockmod
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 300 MHz - 2.40 GHz
  available frequency steps: 300 MHz, 600 MHz, 900 MHz, 1.20 GHz, 1.50 GHz, 1.80 GHz, 2.10 GHz, 2.40 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 300 MHz and 2.40 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.40 GHz (asserted by call to hardware).
  cpufreq stats: 300 MHz:0.00%, 600 MHz:0.00%, 900 MHz:0.00%, 1.20 GHz:0.00%, 1.50 GHz:0.00%, 1.80 GHz:0.00%, 2.10 GHz:0.00%, 2.40 GHz:100.00%[/FONT]

That is the only (although broken) way to get any cpu frequency scaling to work... I need to lower my CPU temps, as they are currently at:

[FONT=Courier New]root@storm:~# sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +47.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +47.0°C  (high = +78.0°C, crit = +100.0°C)  [/FONT]

Google did not help much... Any pointers would be appreciated.

---

### Post by wojox on 2009-12-14
Add:

```
p4_clockmod
```

To:

```
/etc/modules
```

Now, to add the CPU frequency scaling monitor applet to the panel.

---

### Post by dandanio on 2009-12-14
> **wojox said:**
> Add:

```
p4_clockmod
```To:

```
/etc/modules
```Now, to add the CPU frequency scaling monitor applet to the panel.

That is a broken way of doing things. After a recent update to the kernel, p4-clockmod does not allow "ondemand" governor to work properly...

---

### Post by dandanio on 2009-12-16
bump, any help pls?

---

### Post by ToshibaLaptoplinux on 2010-01-17
Same problem, same history.

It really drives me nuts that whenever I upgrade to the next iteration of Ubuntu stuff that worked before breaks.

Any solution for this problem yet?

---

### Post by karlrt on 2010-05-07
did you try /etc/init.d/ondemand start and wait for 60 sec? 

Then you can try to change the ondemand script, at least this was my problem:

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/576022](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/576022)

---

