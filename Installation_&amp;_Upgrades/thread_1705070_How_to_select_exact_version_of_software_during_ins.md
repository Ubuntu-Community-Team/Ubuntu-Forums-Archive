---
title: "How to select exact version of software during installation?"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by Black_Bishop on 2011-03-11
I did horrible mistake and installed upgrade for firefox 3.6.15 via KPackageKit. There would be normally no problem but this version does not work with Q3 live ](*,)
Is there a way to select older version of software in KPackageKit, Synaptic or via dpkg?

P.S. I don't want to install it from tar.gz2 file - I want normal installation.

---

### Post by dabl on 2011-03-11
The only way to "select" an earlier version is to select a different repository, which holds the earlier version and not the newer version.  I don't personally know where you would find that.

If it were a Debian package, there is something called apt pinning that allows one to set a package version and not permit it to be upgraded.  But Firefox is third party, so you're stuck with whatever comes in from Mozilla.  Sorry.

---

