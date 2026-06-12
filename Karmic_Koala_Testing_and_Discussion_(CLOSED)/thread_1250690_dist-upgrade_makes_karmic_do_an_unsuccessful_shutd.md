---
title: "dist-upgrade makes karmic do an unsuccessful shutdown"
date: 2009-08-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by whoop on 2009-08-26
If I do a apt-get dist-upgrade the process wants to remove some files:
cupsddk-drivers foomatic-db-hpijs libgd2-noxpm readahead

If I go ahead and do that karmic will hang at the end of shutdown?
The dist-upgrade has had some files to remove for a while know?
Anybody else having this?

---

### Post by taavikko on 2009-08-27
> **whoop said:**
> If I do a apt-get dist-upgrade the process wants to remove some files:
cupsddk-drivers foomatic-db-hpijs libgd2-noxpm readahead

If I go ahead and do that karmic will hang at the end of shutdown?
The dist-upgrade has had some files to remove for a while know?
Anybody else having this?

Those are all ok to be removed, they're all replaced by other packages.
The shutdow issue is due to the kernel. There's multiple threads about that one.

---

### Post by miegiel on 2009-08-27
> **taavikko said:**
> Those are all ok to be removed, they're all replaced by other packages.
The shutdow issue is due to the kernel. There's multiple threads about that one.

To many shutdown hangs threads :(

From the kernel 2.6.31-7 thread :

> **plun said:**
> Shutdown bug triaged and a milestone to Alpha 5

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/418509](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/418509)

---

