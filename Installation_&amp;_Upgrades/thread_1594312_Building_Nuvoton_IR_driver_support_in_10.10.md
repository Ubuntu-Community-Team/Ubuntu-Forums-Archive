---
title: "Building Nuvoton IR driver support in 10.10"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by supertedster on 2010-10-12
I'm using an Asrock ION 330HT system that comes with a Nuvoton IR receiver. It's not supported in kernel 2.6.35, but there is a [_patch_]("http://people.redhat.com/%7Ejwilson/misc/ir-core-2.6.35/linux-2.6-v4l-dvb-ir-core-update-3.patch") that provides driver support.

Any ideas on where I begin implementing this patch in 10.10? Do I need to remove lirc altogether and build it from scratch? Build a custom kernel?

Edit: see [this thread](http://ubuntuforums.org/showthread.php?p=9972151).

---

