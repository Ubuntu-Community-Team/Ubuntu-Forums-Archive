---
title: "xrandr on Intel destroyed by KMS?"
date: 2009-07-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-07-01
For the past few days, even when I disable KMS, xrandr seems to be mostly broken.

Is anyone else experiencing this?

---

### Post by blackphiber on 2009-07-02
What do you mean when you say broken?

For me I have started having issues with it not listing some resolutions which used to work with my monitor (1680x1050 is gone).

---

### Post by jbernardo on 2009-07-03
What I've noticed is that when you enable KMS, monitor detection is done by the kernel. So, the option "NoDDC" (among others) in xorg.conf are ignored. It might also explain what you're seeing...

---

