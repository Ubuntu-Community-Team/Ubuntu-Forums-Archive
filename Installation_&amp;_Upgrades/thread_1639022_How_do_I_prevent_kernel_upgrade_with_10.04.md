---
title: "How do I prevent kernel upgrade with 10.04?"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by IndieRockSteve on 2010-12-06
I search, and everything I find seems to be "old" information that no longer works.

I currently have,
linux-image-2.6.32-21-generic/lucid uptodate 2.6.32-21.32
linux-image-2.6.32-22-generic/lucid uptodate 2.6.32-22.36
linux-image-2.6.32-23-generic/lucid uptodate 2.6.32-23.37
linux-image-2.6.32-24-generic/lucid uptodate 2.6.32-24.43
linux-image-2.6.32-25-generic/lucid uptodate 2.6.32-25.45
linux-image-generic/lucid-security uptodate 2.6.32.26.28
installed. I wish to not update the kernel on typical distupgrade's, I want to have to use the --ignore-hold command to update my kernel.

I've tried placing a "kernel" file in /etc/apt/preferences.d with the following,
Package: linux-image-generic
Pin: release v=2.6.32.26.28
Pin-Priority: 1001

but that does not seem to work. It seems to be due to the fact that each new kernel image has a different package name that includes the version number.

I then found this and tried this,
Package: linux-image linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
Pin: version 2.6.32.26.28
Pin-Priority: 1001

with no luck.

so, HELP! anyone know how to pin the kernel from being updated?!

---

### Post by zvacet on 2010-12-07
In synaptic find linux-image package with latest number you want to use ( one you don´t want to upgrade) and click on it> file tab >lock version.

---

### Post by IndieRockSteve on 2010-12-10
> **zvacet said:**
> In synaptic find linux-image package with latest number you want to use ( one you don´t want to upgrade) and click on it> file tab >lock version.

I don't want to use synaptic as this is a headless server, I'd prefer to just stick with the command line apps like apt-get

---

### Post by drs305 on 2010-12-10
Take a look at this link (Hold section):
[https://help.ubuntu.com/community/PinningHowto]("https://help.ubuntu.com/community/PinningHowto")

---

