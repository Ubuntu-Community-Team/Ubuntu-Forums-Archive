---
title: "again no sound after partial upgrade"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by Bartje on 2008-02-05
I apparently had to perform a partial upgrade. Again there was no sound anymore. Again I had to re-install alsa manually, because the upgrade didn't use the latest version of alsa. The older version of alsa does not support my, and many others onboard HDA IntelI soundcard. It is starting to annoy me very bad. It is, together with  the 7.10 release the third time I had to manually re-install alsa after an upgrade. Many people have reported this problem already.

I thought I just had to mention this, again, I only can't report it, I'm not a develloper myself.

Most probably we'll have to wait for the Hardy to get it fixed...

Otherwise, I'm still a very happy ubuntu-user.. :-)

---

### Post by frodon on 2008-02-05
You will have to do that after each update and this is also true for any driver you will compile including graphic drivers.
The drivers is compiled for the kernel version you use so if you upgrade to a new kernel this new kernel don't know the drivers you compiled on the old one.

---

