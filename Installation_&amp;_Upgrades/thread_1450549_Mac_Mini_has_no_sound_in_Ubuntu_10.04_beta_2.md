---
title: "Mac Mini has no sound in Ubuntu 10.04 beta 2"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by skhalil on 2010-04-09
Hello Guys! I have just tried Ubuntu 10.04 beta 2 on my Intel Core 2 Duo Mac Mini. Everything is fine except the sound. There is no sound output though the hardware seems to recognize. This was not the problem with 9.10 before. This is the first time I have no sound in Ubuntu. Please help in this regard!

Best Regards,

Syed Khalil

---

### Post by mrdoob on 2010-05-27
Having the same issue with 10.04 Final :(

*bump*

---

### Post by mrdoob on 2010-05-27
Yay, managed to fix it!

> To get the sound working, add the following line to **/etc/modprobe.d/alsa-base.conf**
**options snd-hda-intel model=imac24**

From [here]("http://blog.costan.us/2009/03/ubuntu-810-or-904-on-mac-mini.html").

Apparently was fixed on 9.10, but it's now "broken" again.

---

