---
title: "how do you remove the 386 kernel"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by Slapyo on 2007-03-28
i just figured out how to install the nvidia drivers on to the generic kernel.  now that i am on the generic kernel i would like to remove the 386 kernel from my system.  is this something i can do from the synaptic package manager?  which items do i need to remove so the 386 kernel is fully gone.  thanks!

---

### Post by Slapyo on 2007-03-29
Besides removing the old 386 kernel, is there some sort of "standard" that people follow for holding on to old kernels?  For instance, I have 8-13 of the generic.  Would people hold on to the last 2 kernels, or only the latest kernel, or would you just keep them all?

---

### Post by EmmEff on 2007-03-29
When I upgrade the kernel, I generally keep the last version around for about a month in case I encounter problems.  If there are no problems, I remove it.

Either I'm really lucky or Ubuntu/Linux is that good (I suspect the latter), but I have never had to revert back to an older kernel.

---

### Post by Slapyo on 2007-03-29
How do you remove the old kernels?

Do you go into the Synaptic Package Manager and remove the linux-image-{specific kernel} packages?  Or is there another way?  I'm looking to remove it completely.

---

### Post by EmmEff on 2007-03-29
I use the shell...  'apt-get --purge remove <linux-image-{version}>'

---

### Post by Slapyo on 2007-03-29
great, thanks!

---

