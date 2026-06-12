---
title: "Heads-up: Latest xorg edgers ppa intel driver breaks on GM945"
date: 2009-03-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by TrueTom on 2009-03-08
I had to downgrade, so be careful...

---

### Post by Starks on 2009-03-08
Thanks for the warning.

[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.6.99.1+git20090306.67fef27f-0ubuntu0tormod_i386.deb](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.6.99.1+git20090306.67fef27f-0ubuntu0tormod_i386.deb)

Downgrade to that if you run into problems.

---

### Post by Starks on 2009-03-08
btw, here's the full diff between the two revisions.

[http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/diff/?id=67fef27f4b76490be085d232aba0ca9cbb3c5e59&id2=73aa23d9150121a4e4b70a78cab910acd164abf5](http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/diff/?id=67fef27f4b76490be085d232aba0ca9cbb3c5e59&id2=73aa23d9150121a4e4b70a78cab910acd164abf5)

---

