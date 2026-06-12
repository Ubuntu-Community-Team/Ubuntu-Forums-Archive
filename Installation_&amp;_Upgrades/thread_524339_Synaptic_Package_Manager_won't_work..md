---
title: "Synaptic Package Manager won't work."
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by xxsniperxx31 on 2007-08-13
If I try to open Synaptic Package Manager or anything that uses it, I get this same error.

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So now I can't install anything D:

Can anyone help, please?

---

### Post by Steveway on 2007-08-13
Duh!
$sudo dpkg --configure -a
Should do the trick, did you even read the error message?

---

### Post by xxsniperxx31 on 2007-08-13
> **Steveway said:**
> Duh!
$sudo dpkg --configure -a
Should do the trick, did you even read the error message?

OH I should of known. I just thought there was more to it. Well thanks, it seems like I have a broken package. So I located it, but SPM can't remove it. It says this, "E: sun-java5-bin: Package is in a very bad inconsistent state - you should" And ends at you should. >_<

Any wanna help me? Thanks for the fast response, Steveway.

---

### Post by zvacet on 2007-08-13
**synaptic>edit>fix broken packages**

You have to accept java EULA.If above didn´t work find **sun-java5-bin** in synaptic and try to reinstall it.

---

