---
title: "gutsy kernels"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by orszagh on 2007-10-18
Hi,

I have HP Netserver E60 with 2x PIII CPUs. I have been using Ubuntu 7.04 Server with 2.6.20-16-server kernel and everything was ok. Today I have upgraded to 7.10 Server. After restart the system booted just to the Busybox and hung at initramfs. So I have reboted with old kernel, reinstalled the 2.6.22-14-server kernel and rebooted again. Now the system booted ok, but did not recognize both CPUs. It was running just with one CPU. Now I am running on older kernel from Feisty. I would be grateful if somebody could recommend me which Gutsy kernel to instal to support both Pentium III CPUs. 

Thank you.

---

### Post by tilapia on 2007-10-18
Not sure about the server kernels, but I had a similar problem with my dual Xeon. I had to install the generic kernel as the default 386 one didn't do SMP. Perhaps the same applies to Ubuntu Server?

---

### Post by orszagh on 2007-10-18
Unfortunately, the generic one does not work either (in fact it works but again just with one CPU). I am little bit disapponted because I had the same troubles in Dapper Drake. But the Feisty worked perfectly, so I believed the newer version will be also troubleless.

---

