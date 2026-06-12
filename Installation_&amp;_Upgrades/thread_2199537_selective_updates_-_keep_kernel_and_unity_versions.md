---
title: "selective updates - keep kernel and unity versions"
date: 2014-01-14
forum: Installation &amp; Upgrades
---

### Post by brotakul on 2014-01-14
Hi guys, 

I recently installed 13.10 on an older laptop, runs ok, but the unity and full HD videos are quite sloppy. So i decided to downgrade (fresh install) 12.04 being the latest to support the proprietary AMD fglrx drivers for my Radeon HD 2600 card.

The issue i'm facing is the automatic updates system. Right after installing 12.04, i realize i cannot install all the updates i get for the system, because they might include newer kernel and unity versions that are not supported by fglrx, so i will be downgraded back to the opensource radeon driver from ubuntu.

So, how to update all the other packages (system and user apps, system updates not related to kernel and unity) and still keeping fglrx? Is it enough to do manual updates, unclicking the kernel and unity from the list and install everything else, but somehow be sure that none of the rest of the updated packages do not require the newer kernels and unity? I really don't want to mess up anything, i'm not really good with debugging and fixing the system :)

The easy way around would be not to update anything, but ... i would like to keep the rest of the system up to date.

Thanks guys for future replies.

---

### Post by deadflowr on 2014-01-14
You won't get any newer versions of the kernel or unity or the X-graphics stack(which in your case is important because your card isn't supported for the x stack/fglrx driver after the one used in 12.04.1)(Version 12.04.2 and newer have upgrade X stacks)
The kernel will be of whatever series you installed. Presumably, 3.2 series.
Unity will also be the same, I think Unity 5 on 12.04.

If you installed 12.04.0, or the initial release, but now you system says it is version 12.04.3, or.04, don't worry, you are still using the original kernel series and x stack, those only get upgraded if A) you installed the version point release which has those, and B you installed them yourself.

Don't know if that makes any sense.

---

### Post by brotakul on 2014-01-14
Ok, so you say i can install whatever updates i get from the system and they will not update the kernel, the unity launcher and xserver.

I just finnished installing Ubuntu 12.04.0 (hard to find since almost all 12.04 links redirect to either 12.04.2 or 12.04.3). After installing all my apps i will update the system and get back to you.

Thanks for the reply.

---

### Post by deadflowr on 2014-01-14
Yep.
Of course you'll get some updates for those, but security related for the most part, maybe a bug fix here or there, but even those are usually considered security fixes.
But you won't, let's say, upgrade from the 3.2 kernel series to the 3.5 or 3.8 kernel series.
Those would need to be installed manually, by you.

In case you are interested in upgrading kernel series look here
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by brotakul on 2014-01-15
I updated the system and everything is ok, just as stated in the link above. 

Thank you, deadflowr.

---

