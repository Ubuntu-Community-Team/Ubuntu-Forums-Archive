---
title: "Upgrade from 19.04 to 19.10 hanging"
date: 2019-10-23
forum: Installation &amp; Upgrades
---

### Post by phirst007 on 2019-10-23
My upgrade from 19.04 -> 19.10 appears to be stuck after installing "nvidia-utils-418 (amd64)" using the GUI updater.

The last entry in the terminal window says "e2scrub_all.service is a disabled or a static unit not running, not starting it."

when i run "top" I can see that "eoan" is running but it's been sat like this for 4 hours now, any suggestions?

Cheers

---

### Post by RobGoss on 2019-10-23
Hello and welcome, I think it's best to do a clean installation this way you can avoid issues like this. It's never a sure thing when trying to upgrade from one distribution to another

---

### Post by PaulW2U on 2019-10-23
You seem to have hit a bug in Ubuntu 19.04 which I think been fixed in Ubuntu 19.10.

[https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/1846499](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/1846499)
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=929287](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=929287)

I'm afraid it's beyond me to help fix your installation which by now you've probably abandoned anyway.

---

