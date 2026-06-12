---
title: "Installed SMP kernel, still no SMP!"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by zambizzi on 2006-10-07
I'm trying Ubuntu out again after several years w/ Gentoo.  So far I've had a surprisingly bumpy ride.

First, I just ran all of the updates in the update bubble when it popped up...and the new kernel caused a panic on this machine.  After visiting the forums, I noticed that *many* people had this problem.  I hope this isn't indicative of the Q/A (or lack thereof) that the Ubuntu devs put into the distro?  Anyhow, it easy enough to disable ACPI to prevent the panic from happening again.  However, what would a former Windows user, used to doing Windows updates w/ little, if any trouble think of that as a first time Ubuntu user?  Just some constructive criticism, not flaming.

So, after that, I installedh the i686-smp kernel (and related packages) and I still have no SMP support...why is that?  With Gentoo, when I enabled SMP in the kernel, I get SMP support as I'm using a P4 3.0GHz w/ HT...I've never had a problem w/ any other distro (or Windows.)

How exactly do I go about getting SMP to work in Ubuntu?

Thanks in advance!!

---

### Post by lonce on 2006-10-07
all i did was install smp kernel and it worked.

---

### Post by zambizzi on 2006-10-07
OK, any suggestions for me since it *didn't* work for me?  Both the gnome system monitor and 'top' reveal that I'm running a single proc, not dual.

---

### Post by taurus on 2006-10-07
At the prompt, Applications -> Accessories -> Terminal, see what kernel you are using?

```
uname -a
-or-
cat /proc/cpuinfo
```

---

### Post by zambizzi on 2006-10-07
```

me@mybox:~$ uname -a
Linux mybox 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux

me@mybox:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 3
cpu MHz         : 19496.612
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 6052.84

```

I see the 'ht' flag in there...and it's obviously the correct kernel, yet it shows up as a single kernel in all the instrumentation-type apps, as mentioned before.

---

### Post by taurus on 2006-10-07
I assume that P4 is HT!  I have P4 HT 3.00GHz and gkrellm shows CPU0 & CPU1 with i686 kernel...

---

### Post by zambizzi on 2006-10-07
I installed it and it only shows one for me...simply labeled "CPU" - this issue and a few others (like the kernel panic I mentioned above) are making me think that perhaps I wouldn't be better off w/ Ubuntu...I don't see that I have any less maintenance than I would w/ Gentoo.

I keep hearing about how Ubuntu is a "just works" distro but that has not been so in my experience...and this is my third attempt at using it.

I'm sorry to rant and complain but I'm trying to picture how a Linux "noob" would view Ubuntu after hearing the hype.  There are some obvious problems!

---

### Post by taurus on 2006-10-07
Not sure exactly what you did but it shows CPU0 & CPU1 on my P4 3.00 GHz with HT...  Again, Ubuntu is not for everybody since it works for most but perhaps not for a few others.  That's why there are other Linux distros out there.  Just try the one that works on your machine and stick with it.  Fedora Core 5 is another newbie distro and it's real easy to install and set up.

---

