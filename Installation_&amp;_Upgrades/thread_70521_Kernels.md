---
title: "Kernels"
date: 2005-09-30
forum: Installation &amp; Upgrades
---

### Post by ngms27 on 2005-09-30
I'm a Linux newbie so please be gentle on me.

Is it best to use the kernel that comes with Ubuntu?
Are other kernels more stable?
If other kernels are more statble what would you lose by using then?
How do you make Ubuntu use or give the option to use a different Kernel?

Thanks

---

### Post by mlomker on 2005-09-30
> Is it best to use the kernel that comes with Ubuntu?

It's a lot easier to use a Ubuntu kernel (search in Synaptic for linux-image).  If you have a 32-bit machine it'll install a 386 kernel by default.  If you have a modern machine then you should install the 686 version.

> 
Are other kernels more stable?

No.  Breezy has had a few bad kernels but it's a beta.

> If other kernels are more statble what would you lose by using then?
How do you make Ubuntu use or give the option to use a different Kernel?


That depends upon what you put into them.  The alternative to using a Ubuntu kernel is to actually build your own.  During that process you decide what goes into it.  The downside is that it's easy to make mistakes and it can take a lot of time to get it to work how you want.

There are how-to's on here about building your own kernel.  I wouldn't recommend it until you're comfortable with linux.  Even then it rarely makes sense.  The only people that need to build their own kernels are people with either very old or very new hardware that isn't supported by the current kernel.

---

