---
title: "Unable to update Ubuntu 10.10"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by sequdaz on 2010-10-20
I've been unable to install some of the software center applications and as of late unable to update either, i keep getting similar error messages to this:
```
Failed to fetch http://kw.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/ttf-symbol-replacement_1.2.1-0ubuntu1_all.deb 403  Forbidden
Failed to fetch http://kw.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/wine1.2_1.2.1-0ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://kw.archive.ubuntu.com/ubuntu/pool/main/u/udev/libudev0_162-2.1_i386.deb 403  Forbidden
Failed to fetch http://kw.archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_162-2.1_i386.deb 403  Forbidden
Failed to fetch http://kw.archive.ubuntu.com/ubuntu/pool/main/u/udev/libgudev-1.0-0_162-2.1_i386.deb 403  Forbidden
Failed to fetch http://kw.archive.ubuntu.com/ubuntu/pool/main/u/utouch-grail/libutouch-grail1_1.0.15-0ubuntu1_i386.deb 403  Forbidden

```
Any help is much appreciated. :)

---

### Post by P4man on 2010-10-20
That seems a problem with the mirror. Try another one. Go to your software sources, "download from" and select another mirror.

---

### Post by sequdaz on 2010-10-20
> **P4man said:**
> That seems a problem with the mirror. Try another one. Go to your software sources, "download from" and select another mirror.
oh, it worked. Thanks :)

---

