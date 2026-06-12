---
title: "Verifying 64 bit processor after crashes"
date: 2012-01-23
forum: Installation &amp; Upgrades
---

### Post by okanagansage on 2012-01-23
Hello, I just bought a "business" pc (Optiplex745) on ebay recently which had the hard-drive wiped. I used the following commands from a live-usb to determine whether the processor is 32bit or 64bit. I then installed Lubuntu 64bit and have had a few programs crash on me. VLC crashed on me multiple times playing an mkv and I just had k9copy crash on me. 

The reason I'm questioning whether this is a actually 64bit is because I found the specs for this computer in an online user-guide at [http://support.dell.com/support/edocs/systems/op745/en/UG_en/dt_spec.htm#wp1133451](http://support.dell.com/support/edocs/systems/op745/en/UG_en/dt_spec.htm#wp1133451) which states the Data bus width is 64bits and the Address bus width is 32bits. Which stat determines whether this is a 64bit or 32bit computer?

```
paul@Lubuntu-pc:~$ sudo lshw -C cpu
[sudo] password for paul: 
  *-cpu                   
       description: CPU
       product: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
       vendor: Intel Corp.
       physical id: 400
       bus info: cpu@0
       slot: Microprocessor
       size: 2133MHz
       width: 64 bits
       clock: 1066MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
       configuration: cores=2 enabledcores=2 threads=2

```

```
paul@Lubuntu-pc:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
stepping	: 6
cpu MHz		: 2127.821
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts tpr_shadow
bogomips	: 4255.64
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
stepping	: 6
cpu MHz		: 2127.821
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts tpr_shadow
bogomips	: 4256.00
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

Thanks for any input.

---

### Post by varunendra on 2012-01-24
Any 64bit OS wouldn't install on a 32 bit system in the first place. So yours obviously is a 64bit CPU, which you can also verify here:
[http://ark.intel.com/products/27249/Intel-Core2-Duo-Processor-E6400-%282M-Cache-2_13-GHz-1066-MHz-FSB%29](http://ark.intel.com/products/27249/Intel-Core2-Duo-Processor-E6400-%282M-Cache-2_13-GHz-1066-MHz-FSB%29)
(Notice - Essentials > Instruction Set ----> 64-bit)

As for the crashes, try running them from terminal (for example, type just **vlc** in terminal to run it), keep the terminal while the application is running, then when it crashes, see if it left any error messages in the terminal. Those messages may help determining the cause of the crash.

My first guess is a faulty RAM. You may try to verify it by running 'memtest' from grub menu. Run it for more than 24hrs. if possible and see if it finds errors.

---

### Post by okanagansage on 2012-01-24
Varunendra, thanks for the tip. My primary question was about 32/64 bit so I will mark this as solved. I will test out the memory, too. 

Cheers.

---

### Post by varunendra on 2012-01-24
Cheers! :D

And yeah, it's a good idea to start different threads for different problems. You can always provide links to other ones in them for reference if required.

---

