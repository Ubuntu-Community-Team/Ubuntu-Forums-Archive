---
title: "Kernel upgrades causes system freeze"
date: 2016-05-08
forum: Installation &amp; Upgrades
---

### Post by orionvii2 on 2016-05-08
I've upgraded from Ubunto 15.10 (kernel 3.19.0-15) to Ubuntu 16.04 LTS (inititially installed kernel 4.21???, and installed kernel 4.22??? the next day), both kernels freezes the PC up on booting. The freeze or hang happens at different stages of the boot, occasionally reaching a point where it tries to load X11, but even then it freezes up completely (mouse-cursor doesn't move, pressing numlock on the keyboard has no-effect, and I have to press, and keep the power-button pressed for a few seconds to get the PC to shut down).

Adding "intel_pstate=disabled" and "intel_idle.max_cstate=1" to the kernel parameters in grub manages to halt the freeze until X11 starts to load, but even then the new kernels freeze the PC up. There are no discernible kernel-panic logs in the syslog.

Roughly, the PC specs are:
Intel i5 CPU (Gen 3)
Intel DZ77DHBH-55H (Intel Z77 chipset) mobo
16GB DDR3 RAM
250GB Seagate HDD

I boot with the old kernel (3.19), but would really like to use the latest supported kernel. Any help will be greatly appreciated.

---

### Post by mörgæs on 2016-05-09
I understand the desire to run the latest software but if you have already tried the boot options mentioned I don't have other ideas than to reinstall 15.10.

---

