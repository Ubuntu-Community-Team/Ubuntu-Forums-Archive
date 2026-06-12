---
title: "how-to?: Intel 855GM video card not accelerated"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by cfp999 on 2011-07-29
Just installed Ubuntu 11.04, and everything is perfect, except my video card. Ubuntu 11.04 refuses to run my labtops integrated Intel 855GM video card in OpenGL hardware accelerated mode. Everything is really slow/unresponsive compared to earlier versions, windows are rendering painfully slow etc. From what I can gather, problem is, 11.04/newest Compiz is OpenGL 1.4, and my video card only supports 1.3 (?). Now, I have tried downgrading Compiz following this link:

[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html]("http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html")

No luck so far.. OpenGL is still software only. Do I need to edit some ini-file or xorg.conf, or am I missing something here?

---

### Post by steve11911 on 2011-07-30
Fresh drivers just out...

[http://www.technomagz.com/ubuntu-11-04-intel-855gm.html](http://www.technomagz.com/ubuntu-11-04-intel-855gm.html)

---

### Post by cfp999 on 2011-07-31
Thanks, installed the new driver, but for some reason hardware acc. still won't kick in. Are there any way to force OpenGL hardware rendering?

---

