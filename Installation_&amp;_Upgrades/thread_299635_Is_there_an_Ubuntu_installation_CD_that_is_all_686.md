---
title: "Is there an Ubuntu installation CD that is all 686/smp?"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2006-11-14
I know that once I install Ubuntu (6.06.1 LTS) on my HDD, I can replace the kernel from a 386 one to an optimally compiled 686-smp version.

However, all exectuables already installed on the HDD and even the ones fetched via apt/Synaptic are still ones compiled for 386...

Is it possible to (re) configure my Ubuntu 6.06.1 system so that all the executables on it are compiled for the 686-smp?

Thanks!
Alex

---

### Post by az on 2006-11-14
> **xp_newbie said:**
> I know that once I install Ubuntu (6.06.1 LTS) on my HDD, I can replace the kernel from a 386 one to an optimally compiled 686-smp version.

However, all exectuables already installed on the HDD and even the ones fetched via apt/Synaptic are still ones compiled for 386...

Is it possible to (re) configure my Ubuntu 6.06.1 system so that all the executables on it are compiled for the 686-smp?

Thanks!
Alex

This has been discussed ad nauseam in the past.  There are optimised kernel parameters which make a big difference in performance.  Most of them can now be activated at runtime and not only at compile time.

As for userspace binaries, the compile-time optimizations offer little if not negative performace improvements.  You will not gain any performace by compiling all your apps for 686.

---

