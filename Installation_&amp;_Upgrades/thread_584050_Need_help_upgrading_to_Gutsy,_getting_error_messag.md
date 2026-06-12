---
title: "Need help upgrading to Gutsy, getting error message"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by SlaughterDog on 2007-10-20
When I try to use the automatic updater, I get the following error message:
```
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz 302 Found

```
How do I fix this, or upgrade from the LiveCD (if that's possible)?

---

### Post by Kingfield on 2007-10-20
i got the same message too, maybe the srevers r down.

---

### Post by genterminl on 2007-10-20
There are several other threads on this.  (Unfortunately, I haven't bothered to bookmark them, so I don't have the links handy, but a search of the forums should find them.)  Apparently, the site official name changed from medibuntu.sos-sts.com to medibuntu.org.  I suppose the proper way to change it is to use the "Software Sources" app, on the System/Administration menu.  Click the "Third-Party Software" tab, and then the edit button.  The other way would be to manually edit /etc/apt/sources.list.d/medibuntu.list.

I'm not sure why the upgrade didn't change this (I had the same problem).

---

### Post by Pumalite on 2007-10-20
wrong post.

---

