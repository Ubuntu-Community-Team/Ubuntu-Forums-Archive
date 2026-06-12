---
title: "CPU Scaling not supported in Ubuntu Studio?"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by jredsmyth on 2007-06-15
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=446122&amp;highlight=processor+scaling](http://ubuntuforums.org/showthread.php?t=446122&amp;highlight=processor+scaling) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,
So, I was running feisty, no problem... decided to upgrade to Studio, so I could use it to record music with my band.  Here's the result: I installed studio, no glitches during the install process, THEN when starting the new, freshly installed Ubuntu Studio I, see the splash screen and the status indicator bar, then the monitor goes to black... When I hard reset the computer text flashes onto the screen for a few seconds before it shuts down, it says, "CPU Scaling not supported."  Ok, there's that, then there's the fact that after this my processor and video card are extremely over-heated.  So, hot that I can't touch them.  Okay... who wants/knows how to help me with this?  Any help would be appreciated.
Thanks,
Jared

---

### Post by angryfirelord on 2007-06-15
Open up a terminal and type:
```
sudo powernowd
```
Report what comes out of it.

---

### Post by jredsmyth on 2007-06-15
I would have to boot from the install CD to get a terminal because of the monitor issue when booting from the hard drive... will this still give me the results that you were looking for?
Thanks

---

### Post by angryfirelord on 2007-06-15
Oh, I see. Ok, reinstall Feisty, but when you "upgrade" to Studio, make sure it's not removing anything.

---

### Post by jredsmyth on 2007-06-15
Hi, ok so I just hit esc for grub to not load, and then was able to get to the terminal without having to go through reinstalling feisty. After running 
sudo powernowd
I got this response:

[B]Found one scalable unit: -- 1 'cpu' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

PowerNowd encountered and error and could not start
please make sure that
-You are running a v2.6.7 kernel or later
-That you have sysfs mounted /sys
-That you have the core cpufreq and cpufreq-userspace modules loaded into you kernel
-That you have the cpufreq drivers for your cpu loaded (for example: powernow-k7), and that it works. Check 'dnesg' for errors.[/B]

Also when I run **cat /proc/cpuinfo** this is what I get:

[B]Processor: 0
vendor_id: GenuineIntel
cpu family: 15
model: 2
modelname: Intel(R) Pentium(R) 4 cpu 2.40GHz
stepping: 9
cpu MHz: 2394.207
cache size: 512kb
fdiv_bug: no
hlt_bug no
f00f_bug: no
coma_bug: no
fpu: yes
fpu exception: yes
cpuid level: 2
wp: yes
flags: fpu ume pse tsc msr rae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
bogomips: 4790.30
clflush size: 64[/B]

What should I do at this point?
Thanks, jared

---

### Post by angryfirelord on 2007-06-17
Try
```
sudo apt-get install powersaved
```
That works fine on my Debian system, since powernowd did not.

---

