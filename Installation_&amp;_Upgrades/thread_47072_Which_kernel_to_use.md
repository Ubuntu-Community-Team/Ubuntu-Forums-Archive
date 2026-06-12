---
title: "Which kernel to use"
date: 2005-07-07
forum: Installation &amp; Upgrades
---

### Post by davidU on 2005-07-07
Hi,
 I am installing Ubuntu and have got to the point where I need to choose one of the kernels 

linux-386
linux-image-386
linux-image-2.6.10-5-386

And I don't know which one to choose.  

What is the difference between the 3 kernels ?

Any help would be gratefully received.

regards  DavidU

---

### Post by tonym on 2005-07-07
I think you will find they depend on each other in a chain.  If you install linux-386 it will always depend on the latest version of the kernel so you will get automatic updates when you upgrade.

By the way,  you might want to look at other flavours of Kernel,  depending on your processor type.  For example for an AMD Athlon you'd probably want linux-k7.

---

### Post by davidU on 2005-07-07
Thanks TonyM,
    I am more confused now.

Coming from Windows, a kernel is a conundrum.  

I can follow what a kernel is and that one is required but why a chain ? 

And how come it doesn't matter which one I choose, as someone said earlier.

Why give us dummies a choice when we don't know the answer ?

In the end I went for a default install, and I now have an Ubuntu OS, but it is broken in several places.

Looking to see what I can do with my AMD processor has moved into territory too difficult for my brain and besides, too time consuming.  I'm struggling with a laptop install, and I don't want to kill any more machines just yet.

regards  DavidU

---

### Post by nocturn on 2005-07-07
[QUOTE=davidU]
Why give us dummies a choice when we don't know the answer ?
[/QUOTE]

You are not a dummy (never say such a thing).
Changing kernels is not required (it just gives a speed increase).  If you feel uncomfortabel doing it, just leave the 386 kernel (unless you have 1GB of ram).

---

### Post by tonym on 2005-07-08
The chain of dependencies is there just to make things easier!

If you install linux-2.6.10-5-386 that is the version you wil get.  If a later version comes along you will have to install that yourself.

If you install linux-386 then that will depend on linux-2.6.10-5-386 and so that will be installed.  When a later version of the kernel is available linux-386 will be amended to depend on that version and when you "apt-get dist-upgrade" (or synaptic or aptitude) you will install the later version automatically.

Which version to install depends on whether you want things to happen automatically for you or only fully under your control.

---

