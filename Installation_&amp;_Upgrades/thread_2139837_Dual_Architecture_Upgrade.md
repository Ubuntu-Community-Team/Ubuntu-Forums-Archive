---
title: "Dual Architecture Upgrade?"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by gerowen on 2013-04-28
Just a random observation.  I'm doing an "in-place" upgrade from 12.10 to 13.04, and it seems to be installing a lot of things twice.  For example I see:

```

Setting up libproxy1:**amd64** (0.4.11-0ubuntu1) ...
Setting up libproxy1:**i386** (0.4.11-0ubuntu1) ...

```

For a lot of packages.  Is there a particular reason for this?  Just curious, as long as it doesn't affect system stability I'll trust the updater.

---

### Post by MAFoElffen on 2013-04-28
Most likely cause of that is when you have a 64bit sys installed (arch = x86_64) but somewhere along the line you installed the ia32-libs package... or it was installed when you installed a 32bit package in a 64bit system.  This package's info:
```

This is a transitional package depending on ia32-libs-multiarch, an i386-only metapackage that depends on all of the libraries that were previously included in this package.

```
It allows you to install and run 32bit packages on 64bit systems...

That is how you now have both 32bit and 64bit libraries being installed. For me, that is just normal.

---

### Post by gerowen on 2013-04-28
Ok, that's what I figured.  I'd installed ia32-libs a while back for something, and just left it in there because there's still a handful of applications that are only released in 32 bit.

---

