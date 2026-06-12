---
title: "NVIDIA GeForce Driver"
date: 2013-04-14
forum: Installation &amp; Upgrades
---

### Post by FlyingPies155 on 2013-04-14
I'm trying to install the GeForce 8400 GS driver, and it can't find the kernel path.
I found the kernel source in /usr/include/linux, so I have to put in --kernel-source-path /usr/, but it says that's an invalid path.
Is there another way to do that or something?

---

### Post by MAFoElffen on 2013-04-14
Latest instructions from my sticky:
[http://ubuntuforums.org/showthread.php?t=1743535&p=12397950#post12397950](http://ubuntuforums.org/showthread.php?t=1743535&p=12397950#post12397950)

Current default kernel source_path for nvidia is /lib/modules$/(uname -r)/build/include/ (which installs when you install build-essentials)... Now deprecated was the path /usr/src/$(uname -r). No longer used/current with current Linux formats. It builds a kernel module (kmod)...

Notes:
- Make sure you have the linux-header-<version> from the kernel you are running.
- Then ensure you have the required kernel source packages installed such as build-essentials
* all noted in instructions...

---

### Post by bogan on 2013-04-14
Hi!, **MAFoElffen**,

I think there is a typo in your Post:> Current default kernel source_path for nvidia is /lib/modules[COLOR=#ff0000]$/(uname  -r)[/COLOR]/build/include/ (which installs when you install build-essentials)...  Now deprecated was the path /usr/src/[COLOR=#ff0000]$(uname -r)[/COLOR] That should be:...modules[COLOR=#0000ff]/$[/COLOR](uname -r) and the prior path should be: "/usr/src/[COLOR=#0000ff]linux-headers-$[/COLOR](uname -r)/include".

Chao!, **bogan.**

---

