---
title: "How to automatically install documentation?"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by GordonFreeman on 2010-06-02
Hi,

I'm used from Gentoo that the documentation (info-/man-pages) is installed by default (or at least it's possible to enable it by default for packages that don't do that). However I notice on my Ubuntu installation regularly that a lot of documentation is missing, for example info gcc gives me just the man-page of GCC and not the GCC manual, and for bison I don't get any info documentation.
I'm aware that for these packages there are always *-doc packages, but most of the time I'm realizing that the documentation is missing when I'm offline, so there's no way to just install it then.

So is there a way to automatically install corresponding *-doc packages?


Thanks,

Gordon.

---

### Post by lemming465 on 2010-06-04
Hmmm.  I think I'd try adding```
APT::Install-Suggests "true";
``` to /etc/apt/apt.conf.d/99synaptic.

---

