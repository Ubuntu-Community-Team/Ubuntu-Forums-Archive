---
title: "How to package kernel modules"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by crazydrclaw on 2008-05-25
Hey everyone!  I'm somewhat new to the Ubuntu forums.  I had a question about building kernel module packages.

I've built packages for Ubuntu before, and it's easy enough to do.  Building kernel modules on Ubuntu is also fairly easy.  My question comes in when it comes to which kernel to compile against.  I discovered that even though I installed the i386 version of Ubuntu, it installed the x86_64 kernel anyway, which was a bit surprising.  That means that even if the user installs the i386 release, there's no guarantee that the i386 kernel module package is going to work for them.

In fact, upon inspecting the packages in synaptic, I discovered that there are actually three kernels: linux-image-generic, linux-image-i386 and linux-image-x86_64.

When installing from the alternate CD, it makes use of the generic kernel, and when installing from the ordinary CD, either i386 or x86_64; it appears to always select x86_64, however, if my architecture supports it.

My question is, if I want to build a package that is good for the majority of Ubuntu users, how should I go about packaging things so that it will be as painless for the user as possible?

Thanks!

James

---

