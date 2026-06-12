---
title: "Which Kernel?"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by goseph on 2010-08-02
Hi all!

I am in need of the Radeon power management improvements in linux 2.6.35 and want advice on which I should install into my Lucid?

Here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

There is a 35r1 kernel marked for Lucid from 02 June and a 35 stable kernel marked for Maverick from 02 August.

Which should I use? I don't really want to use an unstable kernel but the stable is marked for Maverick Use. Does that make any difference?

---

### Post by QuinnHarris on 2010-08-02
I would add

deb [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) lucid main

to sources.list or a file in sources.list.d

then install linux-image-generic-lts-backport-maverick

This will install the latest maverick kernel which is 2.6.35.  I use this for better btrfs support.


I am not sure if the newer Radeon power management improvements need to go along with a newer xorg radeon driver.

---

