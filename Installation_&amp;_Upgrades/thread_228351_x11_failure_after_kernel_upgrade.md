---
title: "x11 failure after kernel upgrade"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by kornelix on 2006-08-03
I think this is a bug that should be fixed, but I will ask here before filing a bug report.

I upgraded to the newest kernel 2.6.15-26 using synaptic. The result was that the x-server could not start. I got many cryptic messages at boot time that only an x11 expert would understand. I vaguely remembered running into this problem before, so I booted to the prior kernel and started looking around. In synaptic, I found the "restricted" package labeled "2.6.15-26" and installed it. Problem fixed. 

Question 1: it seems synaptic should take care of this dependency without requiring users to have special knowledge of the necessary extra step.

Question 2: why should a minor version upgrade of the kernel destroy the system? Do the packages in "restricted" contain references to absolute addresses in the kernel that have shifted? What is the underlying problem?

thanks

---

