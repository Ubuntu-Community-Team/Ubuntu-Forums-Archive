---
title: "Cannot Install Guest Additions"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by AhmedAzhar on 2010-01-24
Hey Guys! I am new here and am in lots of trouble.
I installed Ubuntu using Virtual Box 3.0
Everything went smooth with the installation but i cannot install the guest additions.
The manual said something about installing dkms.
So i used this code given.
**sudo apt-get install dkms**
But it gives me these results.
[B]Package dkms is not available, but is referred to by another package.
This may mean that package is missing, has been oblsoleted, or
is only available from another source
E: Package dkms has no installation candidate

[/B]There fore I am unable to install the guest additions. Help me ASAP.

---

### Post by johnzollo on 2010-01-28
I have no idea.  Sorry.  That's a weird problem.  Maybe check in Synaptic Package Manager and double-check your software sources?  I really don't know.  What version of Ubuntu are you using?

-John

---

### Post by mkvnmtr on 2010-01-29
dkms is in the ubuntu.main/com repository. Check that that repository is enabled in your software sources. Then open the symaptic package manager and download and install it.As I remember the manual from Sun mentioned two other packages that are required. You might download and read the manual from the Sun site.

---

