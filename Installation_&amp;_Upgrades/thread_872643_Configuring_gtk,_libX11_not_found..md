---
title: "Configuring gtk, libX11 not found."
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by Karolis5000 on 2008-07-28
So here is the problem. I type ./configure and it shows me this message "configure: error: *** libX11 not found. Check 'config.log' for more details."

But I'm sure I have libX11 installed. How can I fix this? :confused:

Edit: I'm using Ubuntu 8.04

---

### Post by Yannick Le Saint kyncani on 2008-07-28
> **Karolis5000 said:**
> So here is the problem. I type ./configure and it shows me this message "configure: error: *** libX11 not found.

Ubuntu already has a large list of packages available in synaptic. You should install software this way rather than compiling from sources.

However, if you don't have any other choice, headers are available in *-dev packages. You may want to take a look at libx11-dev here.

---

### Post by qywwm on 2011-01-06
you must install Xrender.
[http://cgit.freedesktop.org/xorg/lib/libXcomposite/snapshot/libXcomposite-0.4.3.tar.bz2](http://cgit.freedesktop.org/xorg/lib/libXcomposite/snapshot/libXcomposite-0.4.3.tar.bz2)

---

### Post by MestreLion on 2011-07-29
In my case (using jhbuilder), it was installing **libxext-dev** that made it work

**libxi-dev** package was also necessary

---

