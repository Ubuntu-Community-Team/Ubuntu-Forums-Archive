---
title: "Broken SMP"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by Maintech on 2006-10-28
After upgrading I found my SMP was broken. I am now running off one processor instead of 2. My system is dual xeon. Anyone know how to get the kernel to recognize it is a dual processor without having to hack the kernel?

---

### Post by aurimas on 2006-10-28
I don't know :). I have core 2 duo with msi p965 and also see just one core. I am beginning to think abou compiling vanilla kernel.

---

### Post by louistan3 on 2006-10-28
are you using edgy? afaik, the generic kernel supports smp.. i have a core duo.. and both cores work.. :D

and i think edgy installs 2 kernels in the upgrade.. the generic 2.6.17 and the 386 version.. maybe check the kernel that ur using with > uname -r
and if u are using the 386.. u might like to change the default boot kernel to be the generic one.. which(in my case) works faster and supports smp.. :D hope this helps

---

### Post by aurimas on 2006-10-30
Yes, I'm using Edgy. Fresh install. Generic kernel. And only one core. I also have compiled 2.6.18.1 and results are the same - just one core (SMP was enabled in xconfig).

---

