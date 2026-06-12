---
title: "How to compile 32b bind on 64b os?"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by SkyHiRider on 2010-05-13
I've downloaded Bind source and I need to compile it for my Synology NAS, but my Ubuntu is 64b and I need it in 32b. Any way to pull it off?

---

### Post by lemming465 on 2010-05-14
Several.  The easiest way might be to set up a virtual 32-bit guest and do it in there.
Next easiest might be a [32-bit chroot environment]("https://help.ubuntu.com/community/DebootstrapChroot").
A third way is to set up a cross-compilation environment, see e.g. dpkg-cross.

---

