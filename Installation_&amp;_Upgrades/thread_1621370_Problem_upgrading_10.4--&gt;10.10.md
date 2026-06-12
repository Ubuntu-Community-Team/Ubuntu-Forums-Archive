---
title: "Problem upgrading 10.4--&gt;10.10"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by Easy Limits on 2010-11-14
I am trying to upgrade from 10.4 to 10.10.  I have never had a problem upgrading before with the Update Manager.  Now I get an error message when using the Update Manager.  The message says, "Could not calculate the upgrade".  See screenshots.  I also checked the package manager for broken packages and came up with nothing.

I upgraded my laptop with no problem yesterday.

Any advice?

---

### Post by dino99 on 2010-11-14
sudo dpkg --configure -a

update the synaptic repo tab, then update/upgrade with synaptic

---

### Post by Easy Limits on 2010-11-14
Your suggestion didn't work for me.

---

