---
title: "Version-&gt;V2rsion in config files"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by combinatorix on 2010-02-26
I just recently installed 9.10 out-of-the-box and everything went smoothly
and ran fine.  It then wanted to download and install updates, which I
allowed.  The first time after the updates, the window manager wouldn't
come up because it said it could not write to .ICEAuthority or my home.
I checked permissions on them and they were fine.  I tried everything
in the forums but no luck, so I wiped and re-installed.

The second time, everything went smoothly again, until I installed the
updates.  After updating again, things did not work at all.  After rummaging
around in config files for hours, I discovered that "Version" had been
replaced with "V2rsion" in a couple important config files related to
the package manager.  I'm not sure if this is a typo by a coder, a hiccup
in the network (I have a netgear wireless card), or a bug in the crypto.

Any thoughts?  I was able to correct the problem, but it was extremely
difficult and required a bit of luck on my part.  Before the correction
all the updaters and package fixing stuff didn't function at all.

---

