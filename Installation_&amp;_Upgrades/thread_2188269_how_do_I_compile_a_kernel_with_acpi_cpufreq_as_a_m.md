---
title: "how do I compile a kernel with acpi_cpufreq as a module?"
date: 2013-11-16
forum: Installation &amp; Upgrades
---

### Post by necbot on 2013-11-16
I would like to add the phc-intel module to my kernel so I can undervolt my processor.  I got the phc-intel module compiled into a .deb package successfully and I installed it.  However, to load it, I have to unload acpi by typeing "sudo modprobe -r acpi-cpufreq". When I do this it says I can't unload this because it's built in to the kernel.  Okay, fine, so this means I have to rebuild the kernel with acpi-cpufreq as a module.  

I'm following the [instructions here]("https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel").  I'm at the point where I need to create a config file that specifies that acpi-cpufreq is supposed to be a module.  I ran... 

chmod a+x debian/scripts/*chmod a+x debian/scripts/misc/*
fakeroot debian/rules clean
fakeroot debian/rules editconfigs

I only edited the i386/config.flavour.generic because I'm using 32 bit.  The config editor appears and I go to Power Management and ACPI options -> ACPI (Acvanced Configuration and Power Interface) Support.  My question is...  Am I in the right place and if I am, which settings do I switch from builtin to module?  The processor option seems the likely choice.  However, when I change this to module and save the config file I get the following error when the check-config runs...

check-config: /tmp/tmp.SnaxIwOYEp/CONFIGS/i386-config.flavour.generic: loading config
check-config: /home/user/src/ubuntu-raring/debian.master/config/enforce: loading checks
check-config: FAIL: !exists CONFIG_XEN_ACPI_PROCESSOR | value CONFIG_XEN_ACPI_PROCESSOR y
check-config: 46/47 checks passed -- exit 1

So am I changing the wrong setting in the config?  Am I on the right track to begin with?  Any help would be much appreciated.  Thanks.

---

### Post by tgalati4 on 2013-11-16
What version of linux are you running?

```
uname -a
```

What you do depends on the version.  Older versions of the kernel required a recompile with the undervolt hooks, but I believe the newer versions have the hooks already available.  The check-config error could be that the XEN (virtual machine hypervisor) is incompatible with undervolting, so that would have to be set to No.  

What is the CPU?

---

### Post by necbot on 2013-11-17
uname -a prints "Linux pc 3.8.0-22-generic #33-Ubuntu SMP Thu May 16 15:17:59 UTC 2013 i686 i686 i686 GNU/Linux"

The cpu is an Intel Celeron (Ivy bridge) G1620

---

### Post by tgalati4 on 2013-11-17
Some interesting notes about underclocking Ivy Bridge processors:  [http://www.anandtech.com/show/5763/undervolting-and-overclocking-on-ivy-bridge](http://www.anandtech.com/show/5763/undervolting-and-overclocking-on-ivy-bridge)

Because of the smaller traces in the processor design, you may not benefit as much undervolting as in previous processors.  Proceed carefully.

What is the output of:

```
modinfo phc-intel
```

Is this a dual-boot system?  If so, then run all of Intel's tools first in Windows to determine stability of the processor and motherboard at undervolt, otherwise you will spend several hours of compiling and then spend more hours stability testing.  The Windows tools are complete and you can get the same results in linux, but it requires a lot of work.

Don't expect massive payback, though.  What are your goals for undervolting?

Couple more links:
[http://www.silentpcreview.com/forums/viewtopic.php?f=23&t=64474](http://www.silentpcreview.com/forums/viewtopic.php?f=23&t=64474)

[http://forums.bit-tech.net/showthread.php?t=223382](http://forums.bit-tech.net/showthread.php?t=223382)

What is the output of:

```
cpufreq-info
```

It might look something like:

tgalati4@tpad-Gloria7 ~ $ cpufreq-info
cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]cpufreq@lists.linux.org.uk[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 2.13 GHz
  available frequency steps: 2.13 GHz, 1.87 GHz, 1.60 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.13 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.13 GHz:0.06%, 1.87 GHz:0.00%, 1.60 GHz:0.01%, 1.33 GHz:0.01%, 1.07 GHz:0.01%, 800 MHz:1.36%  (68310)

It is not clear why you need to (re)compile *acpi_cpufreq* as it is part of the current kernel.

---

### Post by necbot on 2013-11-19
Ah, I see, the benefits of undervolting seem to be minor with modern intel cpus.  I was under the impression that acpi_cpufreq was built into the ubuntu kernel.  However, if acpi_cpufreq were a module then I could unload it and load the phc_intel module instead, which is why I wanted to try this.  However, I think I'll pass on undervolting since I'm only doing it to see how low I can get my systems idle power consumption.  I may try undervolting on my AMD APU build, so an answer to how to compile the kernel with the phc module would be great.

---

### Post by tgalati4 on 2013-11-20
For understanding how PHC works, spend some time here:  [http://www.linux-phc.org/forum/](http://www.linux-phc.org/forum/)

The last time I compiled my kernel for PHC and undervolting was a few years ago on Jaunty (9.04), so I presume things have changed.  The basic procedure for compiling the kernel has not changed, but what patches to apply and what modules need modification have changed, so you will have to keep researching.

Here's a how-to for 12.04:  [http://linuxsolver.blogspot.com/2012/05/undervolting-cpu-in-ubuntu-1204.html](http://linuxsolver.blogspot.com/2012/05/undervolting-cpu-in-ubuntu-1204.html)

---

