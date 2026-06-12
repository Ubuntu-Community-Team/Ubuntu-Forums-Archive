---
title: "No graphics w/ kernel 2.6.35-25"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by el_manaba on 2011-02-18
When 10.10 was released, like so many others, I patiently waited until NVIDIA released a compatible 96 driver.  It worked great for a while until I updated to kernel 2.6.35-24.  I learned that kernel was messed up in many ways, so I continued to boot in 2.6.35-23 until 2.6.35-25 was released.  It promises to be more stable, but I still get no graphics when I boot with 2.6.35-25 - just a text interface.

Are there known incompatibility issues with NVIDIA 96 cards and kernel 2.6.35-25 not addressed by the November 2010 driver release?  Or do I just need to re-configure my system in some way?

Thanks

---

### Post by el_manaba on 2011-02-20
Anybody?

---

### Post by el_manaba on 2011-02-23
Did I say something wrong?

---

### Post by philidox on 2011-03-03
> **el_manaba said:**
> When 10.10 was released, like so many others, I patiently waited until NVIDIA released a compatible 96 driver.  It worked great for a while until I updated to kernel 2.6.35-24.  I learned that kernel was messed up in many ways, so I continued to boot in 2.6.35-23 until 2.6.35-25 was released.  It promises to be more stable, but I still get no graphics when I boot with 2.6.35-25 - just a text interface.

Are there known incompatibility issues with NVIDIA 96 cards and kernel 2.6.35-25 not addressed by the November 2010 driver release?  Or do I just need to re-configure my system in some way?

Thanks

I'm having the same issue with the 2.6.35-27 kernel

---

### Post by daviesk24 on 2011-03-21
I'm having the same trouble with nVidia GeForce Go 7300, except that kernel 2.6.35-25 does work.  The ones after it don't work.  I've updated my driver to the 3/7/2011 version, but it did't help.

---

### Post by jimmyjones on 2011-03-21
I have a Geforce MX/MX400 in an old AMD system. I got 96.43.19 from the NVIDIA web site when I first installed 10.10 on the system.

I put the NV~96.43.19.run package in the root directory and every kernel update forced me to telinit 3, sudo sh the package from the command line after boot, no gui.

That all changed in I think kernel .25, maybe .26. I expected to do my usual after the kernel update, surprisingly the system booted to a gui and the 96 drives were in the additional drivers tab as well as in synaptic. I did have to enable the drivers from the additional drivers tab the first time, but it's just worked since then. Looks like the .173 package is also installed according to Synaptic, but it's using .96.

This morning the kernel updated to .28, re-booted to the gui, everything worked.

I'm not messing with it, took too long to get it to work the first time, and it's happy now.

---

