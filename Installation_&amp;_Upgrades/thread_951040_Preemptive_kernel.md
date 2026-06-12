---
title: "Preemptive kernel"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by BogdanRosandic on 2008-10-17
hi 
I'm using Ubuntu 7.10 - the Gutsy Gibbon, it's live CD version which  I have installed on my PC..I'm using kernel which came with distribution, , linux-headers-2.6.22-14..
So my question is: Is my kernel preemptive, how can I found out if it is and enable preemption if it isn't?

Tnx in advance

---

### Post by caljohnsmith on 2008-10-18
All you need to do is install a "realtime" enabled kernel if you want preemption. If you open up Synaptic Package Manager (System > Admin > Synaptic), just select the "linux-restricted-modules-2.6.24-21-rt" package and install it. Also make sure the "linux-ubuntu-modules-2.6.24-21-rt" and "linux-restricted-modules-2.6.24-21-rt" packages get installed too, just in case they aren't considered dependents of the linux-restricted-modules-2.6.24-21-rt package.

And just curious, but why are you interested in preemption capabilities? Is it to optimize music playing/recording on your computer?

---

