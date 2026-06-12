---
title: "Upgrade CPU Issues"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by Xanko on 2010-12-31
Just upgraded to 2.6.35-24-generic-pae and now I am only seeing 1 CPU. I am running a dual-core intel i3-550. Used to show 2 cpu cores and 2 hyperthreads. Any ideas?

cat /proc/cpuid is only showing 1 core.

---

### Post by lithopsian on 2010-12-31
I suspect your  kernel doesn't have SMP support built into it.  You can have a quick look in the kernel config file, grep for CONFIG_SMP I think.  This would be included in most mainstream kernel builds, but I don't know anything about that version or where you got it.

---

### Post by Xanko on 2011-01-03
I see "CONFIG_SMP=y" in the .config for the new kernel listed under /usr/src/linux-headers-2.6.35-23-generic-pae.

I received this kernel update using the Ubuntu Upgrade Manager (i would assume this is the kernel compiled by Canonical)

Also I tried to use Start-Up Manager to boot the previous kernel version and I am still having the same problem.

Also this is my /proc/cpuinfo

> processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i3 CPU         550  @ 3.20GHz
stepping	: 5
cpu MHz		: 1200.000
cache size	: 4096 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 6418.64
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


I have attached a list of the files updated when the system broke.

---

### Post by Xanko on 2011-01-05
> **Xanko said:**
> Just upgraded to 2.6.35-24-generic-pae and now I am only seeing 1 CPU. I am running a dual-core intel i3-550. Used to show 2 cpu cores and 2 hyperthreads. Any ideas?

cat /proc/cpuid is only showing 1 core.

After some further research I believe if have found and corrected the problem. Turns out somewhere along the line my grub config file (**/etc/default/grub**) may have been updated (probably when the new kernel was installed) and also included the following options under **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic nolapic"**. [COLOR="Red"]Turns out that newer systems require apic or lapic to control multi-core chips??[/COLOR] Removing the "noapic nolapic" options and then running **sudo update-grub** would reconfigure grub to boot the kernel correctly. I am now showing all the hardware I had prior to the kernel update. Thank you forums for the help I am just disappointed it took me 3 days for search for that information...

Other threads of interest:

[http://ubuntuforums.org/archive/index.php/t-1142333.html](http://ubuntuforums.org/archive/index.php/t-1142333.html)

[http://ubuntuforums.org/archive/index.php/t-1062918.html](http://ubuntuforums.org/archive/index.php/t-1062918.html)

---

