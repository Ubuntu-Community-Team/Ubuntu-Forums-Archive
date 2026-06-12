---
title: "X-Fi Beta Installation"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by thepocketdrummer on 2007-10-27
I found instructions and a fix

[Here]("http://forums.gentoo.org/viewtopic-t-587921.html")

But, I'm new to this and it is confusing.

So far I've done this...

```
# apt-get install module-assistant
# m-a prepare
# m-a update
```

I need to do this...

```
# tar -xvzf XFiDrv_Linux_US-1.04.tar.gz XFiDrv_Linux_US-1.04/XFiDrv_Linux_US-1.04.tar.bz2
# tar -xvjf XFiDrv_Linux_US-1.04/XFiDrv_Linux_US-1.04.tar.bz2
# chmod -R 755 XFiDrv_Linux_US-1.04
# find XFiDrv_Linux_US-1.04/ -exec touch -c {} \;
# patch -p0 < XFiDrv_Linux_US-1.04_all-in-one_v0.2.patch
# cd XFiDrv_Linux_US-1.04
# ./configure
# make
# make install
```

Pretty please, help.

---

### Post by thepocketdrummer on 2007-10-28
Am I just posting this in the wrong place? :(

---

### Post by thepocketdrummer on 2007-10-29
Please help, I don't know what else I can do...:(

---

