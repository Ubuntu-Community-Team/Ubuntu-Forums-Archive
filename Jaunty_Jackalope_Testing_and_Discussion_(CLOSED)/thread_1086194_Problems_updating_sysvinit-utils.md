---
title: "Problems updating sysvinit-utils???"
date: 2009-03-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mariner09 on 2009-03-03
Is anyone else unable to apply the update to sysvinit-utils?

I get some error messages about it being unable to change some of the files.

---

### Post by crimsun on 2009-03-03
[Bug 336100]("https://bugs.launchpad.net/ubuntu/+source/chkconfig/+bug/336100"), which is really a bug in chkconfig, not sysvinit.

---

### Post by crimsun on 2009-03-03
Fixed and uploaded.

---

### Post by mariner09 on 2009-03-04
Not fixed with sysvinit-utils alone...

I'm still getting the following error when trying to install chkconfig:

E: /var/cache/apt/archives/chkconfig_11.0-79.1-1.2_all.deb: trying to overwrite `/usr/share/man/man8/service.8.gz', which is also in package sysvinit-utils

Unless you plan on patching chkconfig as well, I doubt we'll get a true fix...

---

### Post by crimsun on 2009-03-04
Please read the bug I mentioned; I **did** fix both packages.

---

### Post by crimsun on 2009-03-04
> **mariner09 said:**
> Not fixed with sysvinit-utils alone...

I'm still getting the following error when trying to install chkconfig:

E: /var/cache/apt/archives/chkconfig_11.0-79.1-1.2_all.deb: trying to overwrite `/usr/share/man/man8/service.8.gz', which is also in package sysvinit-utils

Unless you plan on patching chkconfig as well, I doubt we'll get a true fix...

Please note the version of chkconfig that is fixed in jaunty: 11.0-79.1-1ubuntu1. Your error shows an unsupported version that is **not** in jaunty: 11.0-79.1-1.2. Check *apt-cache policy chkconfig* to uncover the origin of that version.

---

### Post by Kow on 2009-03-04
You should just remove chkconfig. It doesn't play nice with new versions of sysvinit, albeit the only conflict is a manpage?

---

### Post by mariner09 on 2009-03-04
That incorrect version came from an internal corporate ubuntu repo.  It's part of our security compliance and I'm trying to find out what the requirement is.

Is this a change for Jaunty only or will Intrepid see this as well?

---

### Post by crimsun on 2009-03-05
> **Kow said:**
> You should just remove chkconfig. It doesn't play nice with new versions of sysvinit, albeit the only conflict is a manpage?

Jaunty's current versions of sysvinit-utils and chkconfig coexist just fine.

---

### Post by crimsun on 2009-03-05
> **mariner09 said:**
> That incorrect version came from an internal corporate ubuntu repo.  It's part of our security compliance and I'm trying to find out what the requirement is.

Is this a change for Jaunty only or will Intrepid see this as well?

It would be worth pursuing StableReleaseUpdates for both source packages, yes.

---

### Post by mariner09 on 2009-03-06
We've opened a bug through our internal process.  The security compliance is for both debian and ubuntu.  The chkconfig versioning they used doesn't match with ubuntu versioning and they are considering options to allow the main ubuntu version to be used as well.

---

