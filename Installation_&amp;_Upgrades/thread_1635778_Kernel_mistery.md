---
title: "Kernel mistery"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by Hawkoon on 2010-12-02
I have been two years on Ubuntu now and there are a couple of things that puzzle me when it comes to installing a new kernel.

Take my netbook. I put Lucid on it which installed with 2.6.32-21. WPA2 didn't work reliably out of the box and someone suggested to install the ppa-mainline kernel 2.6.33.x. I don't know who created it nor whether it is an official thing (I had to download and install it manually) but my WPA2 issues disappeared - so all was good.

Then, couple of days back, update manager tells me to install version 2.6.32-26, which is older than my current running kernel! Why should I want to install an older version than what I am running on? Anyway, I did, thinking that maybe, for some undefinable reason it is better (like better maintained?) than my current ppa kernel. The WPA2 support was broken again however, so I quickly switched back to my ppa kernel.

When I look through synaptic now, I see that version 2.6.35-22 is available. So that is actually newer than my current ppa kernel. But my update manager doesn't want to install it. What is it waiting for?

So summing up my questions,

what is the difference between a "standard repository kernel" and ppa mainline kernel

why offer installation of kernel that is older than running one

why is latest available kernel held back by update manager when I can see it in synaptic?

If someone could shed some light about this kernel business I'd be more than grateful.

---

### Post by snowpine on 2010-12-02
It is pretty simple, really...

If you don't want any more updates to the 2.6.32 kernel, you can remove it using Synaptic.

If you want the 2.6.35 kernel, you can install it using Synaptic.

In other words, the system treats different kernels like different packages, not as newer versions of the same package. This allows you to have several kernels installed at once if you choose.

If your current kernel works well for your needs, then there is no reason to install a newer kernel, in my opinion.

---

### Post by Hawkoon on 2010-12-02
Thanks snowpine, I am feeling enlighted now :)

I never differentiated between kernel versions (x.y) and updates within a kernel version (x.y-z). It all makes sense now. Cheers.

But what about ppa mainline kernels. Someone privately bakes a new kernel and shares it, but why call it mainline. There seems to be more to it than meets the eye, nope?

---

### Post by snowpine on 2010-12-02
All Ubuntu releases have their kernel "frozen" for the life cycle of the release. For example 10.04 will use some variant of the 2.6.32 kernel for the entire 3 years it is supported.

The PPA allows you to easily install a newer kernel if you choose (for example if it offers better support for your wifi card). That's really all I know about it; I'm not sure the exact meaning of "mainline" in this case. :)

---

### Post by Hawkoon on 2010-12-02
Thanks for taking time to share your infos. Solved and out.

---

