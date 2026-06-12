---
title: "Does the Beyond kernel patch suck?"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by gribelu on 2006-12-22
I spent the last two days compiling kernels (i think i'm becoming a geek). My first time btw ](*,) 

Tried the 2.6.19 kernel with the [Beyond2 Patch]("http://iphitus.loudas.com/beyond.html") wich also updates it to 2.6.19.1.
My main problem was that the system had very weird latencies with this new kernel.
I tried using the "voluntary kernel preemption" scheduler , then the "preemptible kernel"... enabled/disabled SMP and "preempt the big kernel lock" etc... 
But the system always stalled/stuttered under high load. Especialy when some swap was in use.
Now, finally, i decided to compile the vanilla 2.6.19.1 kernel, no patches.. And it works great! Why is that?
My guess is that the culprit is the "Staircase scheduler" wich is part of the [CK patch]("http://members.optusnet.com.au/ckolivas/kernel/") (it comes with the Beyond pack)

Any thoughts on the subject? Btw i'd be interested in any ideas related to kernel latency... schedulers and such.. I want a snappy system! :rolleyes:

Thanks

---

### Post by T-One on 2006-12-22
I had the EXACT same problem you're talking about, and I couldn't figure out why. It wasn't really noticeable under normal use, but when I fired up a VMWare machine, it would sit there, then when the system went into idle, the VM would start pegging the hard drive. For 20 minutes at a time.

Vanilla kernel doesn't do this at all.

Anybody know of a patchset that doesn't use CK patches?

Edit: I'll try reversing the Staircase patch and see if that works...

---

### Post by gribelu on 2006-12-22
You can also download [individual patches]("http://iphitus.loudas.com/beyond/2.6.19/2.6.19-beyond2/patches/") and maybe try to hack the code of the ck patch... or maybe... it has some sysctl parameter that we could set?
Please post your results.. i had enough compiling for now :-#

it has /proc/sys/kernel/interactive and /proc/sys/kernel/compute ... but no way to disable it. Or there is such a thing but there's nothing on the homepage about it. Try reversing it

---

### Post by gribelu on 2006-12-22
hmm i found this on a forum... worth a try!
> If you want to give a try to CK patchset disable preemption. At last on my system preemption + ck works in a realy weird way and suprising slow.

In general ck gives a MUCH better results than preempt enabled kernel ... of coz if you want to patch your kernel with 3rd patches :)

---

### Post by T-One on 2006-12-22
I just found something interesting in the Gentoo forums:
[http://forums.gentoo.org/viewtopic-p-3797178.html#3797178](http://forums.gentoo.org/viewtopic-p-3797178.html#3797178)

> My laptop locks up when I launch a vmware session under 2.6.19-beyond1/2.  2.6.17-beyond4 still works great.     
VMWare needs to be updated for 2.6.18/9 series kernels. Check that your version is the latest. WFM.I'm using VMWare Workstation 5.5.3, which is the latest AFAIK.

I'm going to test a 2.6.19 vanilla (with Suspend2 and fbsplash patches) to see if this continues.

---

### Post by gribelu on 2006-12-22
i think vmware is known to be incompatible with 2.6.19 kernels :-k

---

### Post by gribelu on 2006-12-23
Ok so i couldn't help myself... i compiled two more times.
- Kernel 2.6.19.1 vanilla .. I had the best latencies with Voluntary Kernel Preemption + SMP Enabled + Preempt Big Kernel Lock enabled. I have a sempron so i enabled SMP just because otherwise "Preempt big kernel lock" gets disabled. The "Preemptible Kernel" scheduler stutters too much when there's lots of disk access.

- Kernel 2.6.19-beyond2 .. best latencies with the standard Preemption disabled, SMP enabled and Preempt Big Kernel lock enabled. Tried it without SMP and it stuttered much more.

I'll stick to the Beyond kernel for now as it seems to do a nice job. But then again i didn't have time to test it too much.
Most users shouldn't notice much of a difference between the vanilla with Voluntary Kernel Preemption and the Beyond. I use the firefox/flash/audio bug.. with pandora.com.. for testing purposes :mrgreen:

Edit: Now that i think of it... enabling IO/APIC might have a negative impact on my system's latency. I don't really remember at wich point i enabled/disabled it i'm just saying this in case it really is relevant, to avoid confusion. Might be that i disabled it when i enabled "Preempt Big Kernel Lock" and SMP support... the conclusion is that i'm not sure wich one made the small and final difference wich made me declare the Staircase Scheduler the winner on my system.

---

