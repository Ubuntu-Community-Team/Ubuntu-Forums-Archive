---
title: "Linux Image k7"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by Goodkimchee on 2008-02-29
Hi.  I'm trying to upgrade my kernel from the 386 kernel to the amd k7 image, but when i look for it with synaptic it's not there.  Where can I get it?  

Also, I was wondering if I should upgrade to the amd64 kernel as I'm running an amd64 3000+ core.  I'm not really keen on doing that, however, because I keep hearing about program/software incompatibilities, and I figure that the k7 kernel would give me a great boost from the 386 kernel, without all the problems.  

Any and all help would be muchly appreciated.  Thanks.

---

### Post by hyperair on 2008-02-29
If I'm not mistaken, the developers have removed that kernel, along with the i686 kernel in favour of the generic kernel. Apparently there is negligible performance difference of the i686 or k7 kernel (on respective platforms) compared to the generic one.

---

### Post by Goodkimchee on 2008-03-04
Hi.  Thanks for the reply.  Can you explain that one?  Why would there be a negligible difference in two cores that are more than a decade apart?  I'm having a hard time wrapping my brain around that one.

---

### Post by hyperair on 2008-03-05
Firstly, I'd like to mention that the generic kernel is not "more than a decade apart" from the specialized kernels. They're from the same kernel version, but with different configuration options enabled. The specialized kernels would have just optimizations for the architecture it is meant to be run on, whereas the generic kernels have optimizations to run on all architectures. Because the linux kernel is coded in a rather modular manner, having optimizations for other architectures as well as the one it runs on would not cause a significant difference in performance. Perhaps a few milliseconds or microseconds, but not more than that.

---

