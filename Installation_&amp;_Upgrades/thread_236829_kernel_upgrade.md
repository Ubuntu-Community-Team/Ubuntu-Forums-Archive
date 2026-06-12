---
title: "kernel upgrade"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by striketh on 2006-08-15
Hello..I want to get the 2.6.17 kernel in dapper. However, I've never compiled a kernel and after reading a few guides it seems a bit confusing. I was wondering if there's an easier way to upgrade? Are there any pre-compiled .deb packages I can download? Or..would changing the synaptic sources to edgy and upgrading only the kernel work?

Thanks.

---

### Post by tseliot on 2006-08-15
> **striketh said:**
> Hello..I want to get the 2.6.17 kernel in dapper. However, I've never compiled a kernel and after reading a few guides it seems a bit confusing. I was wondering if there's an easier way to upgrade? Are there any pre-compiled .deb packages I can download?
If you follow this guide you will need to open Terminal and copy and paste commands (and of course select things using your mouse).
[http://www.ubuntuforums.org/showthread.php?t=217657](http://www.ubuntuforums.org/showthread.php?t=217657)


It's not difficult.

> **striketh said:**
> Or..would changing the synaptic sources to edgy and upgrading only the kernel work?
That would only break your system.

---

### Post by striketh on 2006-08-15
eh..i tried compiling and this is what i ran into:

drivers/media/dvb/ttpci/budget-av.c: In function ‘frontend_init’:
drivers/media/dvb/ttpci/budget-av.c:1063: error: ‘struct budget_av’ has no membe r named ‘reinitialise_demod’
drivers/media/dvb/ttpci/budget-av.c:1068: error: request for member ‘tuner_ops’ in something not a structure or union
drivers/media/dvb/ttpci/budget-av.c:1068: error: ‘philips_cu1216_tuner_set_param s’ undeclared (first use in this function)
drivers/media/dvb/ttpci/budget-av.c:1068: error: (Each undeclared identifier is reported only once
drivers/media/dvb/ttpci/budget-av.c:1068: error: for each function it appears in .)
make[5]: *** [drivers/media/dvb/ttpci/budget-av.o] Error 1
make[4]: *** [drivers/media/dvb/ttpci] Error 2
make[3]: *** [drivers/media/dvb] Error 2
make[2]: *** [drivers/media] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.17.7'
make: *** [stamp-build] Error 2

thoughts?

---

