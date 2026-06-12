---
title: "Backports wireless on Natty"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by redmaniac on 2011-07-02
Hi,

I'm not really sure if this is the right place to post this question but it seemed to fit best.

Does anyone know if/when the backports wireless modules for Natty will be released? I was just wondering because the latest ralink rt3090 driver (which is basically the rt2860 driver) cannot be compiled 'as is' with the 2.6.38-8 headers (some enum it uses has been moved and there are probably other things that I don't know of). The present rt2860 drvier shipped with Natty is pretty much ancient and has severe issues with connectivity (see numerous threads in this forum).

cheers
redmaniac

---

### Post by dino99 on 2011-07-02
try with the latest kernel 3.0.3 (rc5)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

