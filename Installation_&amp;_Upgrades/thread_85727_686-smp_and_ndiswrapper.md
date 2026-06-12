---
title: "686-smp and ndiswrapper"
date: 2005-11-03
forum: Installation &amp; Upgrades
---

### Post by markr on 2005-11-03
I've just upgraded my system to the 686-smp kernel (along with the headers, restricted modules etc).

However, when I try to start Ubuntu with the new 686-smp kernel it hangs when trying to start my network (ndiswrapper).

If I start using the 386 kernel, it works fine.

I removed all my ndiswrapper configuration and then restarted using the 686 kernel,   this worked fine.

Whilst running the 686 kernel I setup ndiswrapper again and rebooted; hung at the same place!!!!

My question is, do I need to do anything special to get ndiswrapper working with the 686 kernel

Thanks

Mark.

---

### Post by az on 2005-11-03
No, you shouldn't.

---

### Post by markr on 2005-11-04
hmmm..

any thoughts on what the problem could be then?  I realise I haven't provided much in the way of detail, but I am not sure what logs will be useful for tracking the problem with this.

Would it be recommended to get the latest ndiswrapper source code and build it from scratch?

Mark.

---

### Post by markr on 2005-11-09
Okay,  still having this problem,  but may be getting a step closer.

The only difference I can see in the logs that would cause ndiswrapper to stop my system starting with a 686-smp kernel is the fact that ndiswapper seems to be starting with two options.

386 Kernel - ndiswrapper preempt=No, SMP=No
686-smp Kernel - ndiswrapper preempt=No, SMP=yes

Does anybody know what affect this option has (SMP) and how I can turn it off and see if that resolved the problem?

Thanks

Mark.

---

### Post by markr on 2005-11-09
Just tried disabling hyperthreading at BIOS level,  but the same problem occurs.  Any advice greatfully accepted!

---

