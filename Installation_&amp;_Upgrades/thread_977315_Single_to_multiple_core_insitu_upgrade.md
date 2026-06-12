---
title: "Single to multiple core insitu upgrade?"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by dombaines on 2008-11-10
Daft question perhaps.

Can Ubunutu cope (running 8.0.4 now on a single core 64 bit AMD 3500+, 4GB RAM and lots of SATA disks) with an upgrade of H/W from AMD single core 64 bit to dual or quad core 64 bit CPU, will also include a 2x or 4x memory at same time? Automatically?

Or is it better to forget about what is there now and reinstall from scratch?

It is a PC although system is basically used as a VMware server host, so will shut down all guests and rebuild/reinstall them as needed (50% are different versions of windows). I suspect will have to rerun vmware-config.pl too as the kernel will/may(?) have changed. However the system is also used for a few other tasks in purely workstation mode and might be better if didn't have to reinstall/reconfigure it.

Thanks.

Dom

---

### Post by prshah on 2008-11-10
> **dombaines said:**
> 
Can Ubunutu cope (running 8.0.4 now on a single core 64 bit AMD 3500+, 4GB RAM and lots of SATA disks) with an upgrade of H/W from AMD single core 64 bit to dual or quad core 64 bit CPU, will also include a 2x or 4x memory at same time? Automatically?


It should cope easily; Ubuntu (linux) does not follow a pattern of "cached" hardware drivers, but redetects all hardware every startup.

However, you _may_ have to manually enable a suitable CPU governer (such as powersave or ondemand). Very easy, requires only a single command or so, post back if you need it after the upgrade.

---

### Post by dombaines on 2008-11-10
Thanks,

Not too fussed about the drivers for H/W but the essential Single to SMP CPU change. It used to be that linux required a kernel recompile if this happened. Is the stock distribution kernel SMP capable 'out of the box?'.

I cannot see SMP in the package manager so just don't know.

Dom

---

