---
title: "Issues with alsa-driver-linuxant for instals/upgrades"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by shabado9889 on 2011-03-04
First I had issues with my sound with my driver and created this question [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/147473](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/147473) 

Then I upgraded but now (and during the upgrade) I receive this error for any updates or installs:
Errors were encountered while processing:
 alsa-driver-linuxant
E: Sub-process /usr/bin/dpkg returned an error code (1)

I checked out the log for alsa-driver-linuxant and after a few remove lines of code it has this in the log:

The file /lib/modules/2.6.35-27-generic/build/include/linux/autoconf.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/2.6.35-27-generic/build).

What are my steps to fix this so my system (and installs) can run smoothly? What info should I add to help this make sense?

---

