---
title: "Increasing disk space on a Wubi installation"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by jarble on 2011-03-01
Is it possible to increase the disk space for a Wubi installation?

---

### Post by bcbc on 2011-03-01
It's possible [http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

Most people recommend moving to a regular Ubuntu (partition) install if you intend to use Ubuntu permanently. Wubi is great to try out. It's possible to migrate wubi to partition: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by jarble on 2011-03-02
The last time I tried setting up an Ubuntu partition, my Windows partition remained installed but became unusable, and some of my computer's hardware didn't work with Ubuntu. Is there any straightforward, fail-proof way to prevent this from happening again?

---

### Post by bcbc on 2011-03-02
> **jarble said:**
> The last time I tried setting up an Ubuntu partition, my Windows partition remained installed but became unusable, and some of my computer's hardware didn't work with Ubuntu. Is there any straightforward, fail-proof way to prevent this from happening again?

Hard to say - since I don't know what was wrong. If hardware doesn't work it shouldn't make a difference whether it's wubi or normal.

There's nothing wrong with using wubi as long as you 1) lock the grub-* packages and 2) backup anything you can't afford to lose (that's good practice anyway, but the wubi root.disk is less reliable than a true partition)

---

