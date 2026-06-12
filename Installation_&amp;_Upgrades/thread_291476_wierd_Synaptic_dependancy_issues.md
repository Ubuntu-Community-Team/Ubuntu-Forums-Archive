---
title: "wierd Synaptic dependancy issues"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by DirtDawg on 2006-11-02
After failing miserably at finding a GTK based browser that doesn't suck, I decided to try Amaya. It's in the repos, but when I try to install through synaptic, I get this error:
```
 Depends: libpng10-0 (>=1.0.18) but it is not installable
```

I have libpng12-0 installed, and all the major repositories are enabled. I found a deb package of libpng10-0, but it's from 2004 and I'm not sure it's a good idea to install it.

Anyone know how to resolve this? Thanks.

---

### Post by DirtDawg on 2006-11-02
I ended up installing the libpng10-0 manually, but now a get a complaint about gdk-imlib1. When I try to install that manually, it says it conflicts with libpng10-0. What gives!? Are my repositories mucked up? I turned on all available repos, but that didn't seem to help.

I've never experienced this sort of problem before with apt-get. It usually works perfect.

---

### Post by DirtDawg on 2006-11-02
Well I think I've --sort of-- figured out what's wrong. According to the [package page]("http://packages.ubuntu.com/dapper/web/amaya") for Amaya, the ppc version (which I need) requires libpng10-0, which is no loner available.

So I guess I'm out of luck. Kind of lame, but as a ppc user I'm getting more and more used to the feeling.

---

