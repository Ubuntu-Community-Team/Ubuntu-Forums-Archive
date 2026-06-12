---
title: "Linux Kernel Unbootable"
date: 2013-03-31
forum: Installation &amp; Upgrades
---

### Post by Fynn on 2013-03-31
I've been successfully running kernel version 3.5.0-26-generic for some time now.  Yesterday I changed a couple of things (tried to install Firefox and Moonlight, maybe did a few other things) and my mouse started tracking strangely across the screen.

Tried to reboot, and my box just gave me a black screen, couldn't ssh to it either.

I've been able to boot into 3.5.0.25-generic.

Can anybody tell me how to reinstall or repair 3.5.0-26-generic? (I already tried apt-get update && apt-get upgrade).

Update - tried recovery mode, but that freezes after an "end trace" statement - doesn't get as far as booting up.

---

### Post by Fynn on 2013-03-31
OK, so did apt-get remove linux-image-3.5.0-26-generic and then reinstalled it. Seems happier now.  Weird.

---

