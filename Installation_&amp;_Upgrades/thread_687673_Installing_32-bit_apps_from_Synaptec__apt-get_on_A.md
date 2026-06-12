---
title: "Installing 32-bit apps from Synaptec / apt-get on AMD64"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by zaius55 on 2008-02-04
Hello,

Recently has moved to ubuntu from being a long time gentoo user on AMD64.  Was curious if I can setup a repository for 32-bit applications to run in IA32 emulation mode?  It seems as though some apps haven't made the transition.

Thanks!

---

### Post by dabl on 2008-02-04
The difference between 32-bit packages and 64-bit packages is "invisible" to the *buntu user.  If you installed the 64-bit OS, then just open Synaptic and get the packages you want -- the package manager knows what your arch is.

The only time you'll bump into issues with the 64-bit OS is when you try to get external/downloaded apps to install.  :)

---

### Post by zaius55 on 2008-02-04
So packages that are available in 32-bit binaries and NOT 64-bit binaries will show up in the package manager?  That doesn't appear to be the case.

---

### Post by dabl on 2008-02-05
Nope -- I didn't say or mean that.  The package manager will show you applications packaged for your architecture, be it 32-bit or 64-bit.  If there's not a package available for your architecture, then Synaptic or apt-get (or Adept or aptitude) won't show it, thus you won't install it.  That's part of how the package manager keeps us from borking our systems (or tries to).   :lolflag:

---

