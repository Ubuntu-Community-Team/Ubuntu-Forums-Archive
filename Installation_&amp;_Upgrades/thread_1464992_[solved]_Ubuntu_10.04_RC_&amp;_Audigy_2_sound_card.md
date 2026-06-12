---
title: "[solved] Ubuntu 10.04 RC &amp; Audigy 2 sound card fix"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by TBerk on 2010-04-28
Turns out you will need to (re)install **gnome-alsamixer** to gain access to the *Audigy Analog/Digital Output Jack*, that which when toggled (sometimes On, Sometimes Off will do it) will allow wonderful sounds to flow from the speakers.

[http://www.ubuntugeek.com/fix-for-no-sound-sound-blaster-audigy-after-upgrading-from-ubuntu-9-04-to-9-10.html](http://www.ubuntugeek.com/fix-for-no-sound-sound-blaster-audigy-after-upgrading-from-ubuntu-9-04-to-9-10.html)

Oh, and btw- In my particular case I had nuked my / partition but retained my /HOME partition. This might mean when I upgraded in place the 9.10 to beta2 10.4 RC, then later nuked the OS and reinstalled from CD, I might have retained some settings, config files in the /HOME partition that informs my 'solution'. just fyi.


berk

---

