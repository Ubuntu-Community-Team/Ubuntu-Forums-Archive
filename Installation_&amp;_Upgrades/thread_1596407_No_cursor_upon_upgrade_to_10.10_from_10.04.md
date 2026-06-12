---
title: "No cursor upon upgrade to 10.10 from 10.04"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by not1 on 2010-10-14
Hey guys,

I recently upgraded my old and tired Toshiba Portege M300 to the latest Ubuntu release.

The fist time I logged in I browsed the web for a bit, changed my refresh rate and theme. There was significantly lower performance. For example Youtube videos "skipped", moving my cursor "skipped". It was like the ram was being pushed more than usual or something.

There **was** a cursor in this session. When I restarted there wasn't one and there hasn't been one since. The internet has yet  to help me with this issue or imply that someone else has this bug.

Can I easily "downgrade" or otherwise solve these two problems? No visible cursor is especially annoying. I have to use that ctrl button function that shows you where it is.

Thanks guys :)

---

### Post by Bambabur on 2010-10-16
Dear guys, 
the problem is in drm module in the kernel linux-image-2.6.35-22-generic provided with Ubuntu 10.10.
To solve the problem, you can install another kernel from PPA :

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.7-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.7-maverick/)

It worked for me!

My video card is :

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

Bye

Bambabur

---

