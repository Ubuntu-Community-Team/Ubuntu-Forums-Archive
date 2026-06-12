---
title: "Hardy - Generic or 396 kernal?"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by chamstar on 2008-05-09
Hi, I recently upgraded to the latest Ubuntu (Hardy Heron) the upgrade happened but two things stopped working, firstly no matter how I try I can't get the Nvidia drivers to work (I have dual screen) and secondly my Windows VM in VirtualBox stopped booting.

I noticed that I could cure all these problems by selecting my previous kernel at boot time. I also noticed that all previous (and working) kernels are 'generic', the new one is '386'. Is this right/wrong?

The boot loader options look like this:

Ubuntu 8.04, kernel 2.6.24-16-386
Ubuntu 8.04, kernel 2.6.24-16-386 (recovery mode)
Ubuntu 8.04, kernel 2.6.22-14-generic
Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.20-16-generic
Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)

Many thanks, Cham.

---

### Post by brigux on 2008-05-09
For your Windows VM, run:
/usr/bin/vmware-config.pl

---

### Post by chamstar on 2008-05-12
Thanks brigux, I wonder do you know if the kernel should be generic or 386?

---

### Post by brigux on 2008-05-12
386 kernel is compatible with old processors 
generic kernel automatically detects which processor is running and will use the appropriate optimizations.

So, unless your have an old or undetected CPU you should use the generic one.

---

### Post by chamstar on 2008-05-12
I used the update manager to upgrade I wonder why it choose 396 instead of generic. Im on Intel so it should work either way?

Thanks for your help.

---

### Post by brigux on 2008-05-12
Unless if you have specific needs or issues, I would suggest not to worry about that.

I'd be happy to read someone else comments about that tho..

---

