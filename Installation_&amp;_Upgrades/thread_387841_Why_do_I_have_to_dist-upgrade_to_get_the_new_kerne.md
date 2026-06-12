---
title: "Why do I have to dist-upgrade to get the new kernel?"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by Levander on 2007-03-18
I'm running 2.6.17-10 right now.  And apparently, when I "sudo aptitude upgrade" it says it's holding back a few kernel package upgrades to 2.6.17-11.

Reading around, it looks like I'm supposed to dist-upgrade to get the new kernel instead of the way it used to be, where I used to just do a regular upgrade to get new kernels.

Why do I have to dist-upgrade to get the new kernel?

---

### Post by vayde on 2007-03-18
'upgrade' upgrades most of your packages.  If something goes drastically wrong, one piece of the machine might break, but the rest will still function.

Kernels, are a bit more touchy.  If you were to upgrade the kernel, things could break and be difficult to fix.  Hence it won't upgrade the kernel unless you specifically tell it to.

The difference is complicated by the fact that update-manager apparently does dist-upgrades by default.

---

### Post by scxtt on 2007-03-18
you can upgrade your kernel independent of "upgrade" or "dist-upgrade" ... just search for the kernel you want to install, then install it ... if it gives your problems, just boot your "old, previously working" kernel ...

---

### Post by Levander on 2007-03-18
Okay, thanks guys.

So, now I'm looking at why I'd bother to upgrade to the new kernel.  'sudo aptitude changelog linux-image-generic' says, "ABI bump to -10." for the new 2.6.17-11 version.

What's an ABI and why do I care if they've bumped it?

---

### Post by vayde on 2007-03-18
ABI:  Application Binary Interface.  

I don't know specifically what it does, but if there's a newer one, and programs are expecting the new version, it might be a good idea to upgrade.  

Pro's /Cons are way over my head.

---

### Post by scxtt on 2007-03-18
in my view, if there isn't a SPECIFIC reason to upgrade your kernel (2.6.17-11 now supports "X", but 2.6.17-10 doesn't) - don't bother ...

i really doubt the minor updates done b/t revisions (2.6.17 --> 2.6.18) will make much difference in your day-to-day ubuntu'ing ...

---

