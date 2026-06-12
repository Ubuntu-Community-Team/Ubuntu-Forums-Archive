---
title: "Will Firefox in Ubuntu 9.10 have tracemonkey enabled?"
date: 2009-09-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by parameter on 2009-09-27
I head read that Mozilla didn't enable the tracemonkey javascript engine in their binary linux builds of Firefox 3.5. Will Ubuntu 9.10's version of Firefox 3.5 be compiled with tracemonkey support?

---

### Post by quazi on 2009-09-27
It's already enabled in 32-bit versions of Firefox 3.5 in Jaunty.  It is not enabled in 64-bit versions.

---

### Post by parameter on 2009-09-27
> **quazi said:**
> It's already enabled in 32-bit versions of Firefox 3.5 in Jaunty.  It is not enabled in 64-bit versions.

Will I be able to install the 32-bit version in my 64-bit OS?

---

### Post by andrewabc on 2009-09-27
> **quazi said:**
> It's already enabled in 32-bit versions of Firefox 3.5 in Jaunty.  It is not enabled in 64-bit versions.

Umm, will this change? I currently use 64 bit, and if it's not enabled it is yet another reason not to use 64 bit.

Have they even enabled [PGO](http://en.wikipedia.org/wiki/Profile-guided_optimization) yet that windows firefox has?

---

### Post by parameter on 2009-09-27
> **andrewabc said:**
> Umm, will this change? I currently use 64 bit, and if it's not enabled it is yet another reason not to use 64 bit.

Yes, I imagine that it will change. I've been doing some googling since posting my original question. I've found that 64-bit tracemonkey is enabled in the recent tracemonkey builds. I assume this will make it into a future release. According to the blog post by the mozilla developer who did the work, [he's seeing a 20% increase in performance]("http://www.bailopan.net/blog/?p=595") over the 32-bit tracemonkey build.

---

### Post by CoreyB. on 2009-09-27
> **parameter said:**
> Yes, I imagine that it will change. I've been doing some googling since posting my original question. I've found that 64-bit tracemonkey is enabled in the recent tracemonkey builds. I assume this will make it into a future release. According to the blog post by the mozilla developer who did the work, [he's seeing a 20% increase in performance]("http://www.bailopan.net/blog/?p=595") over the 32-bit tracemonkey build.

By future release do you mean 9.10 final or something after that?

---

### Post by parameter on 2009-09-28
> **CoreyB. said:**
> By future release do you mean 9.10 final or something after that?

I mean a future release of Firefox. Maybe FF v4.

---

### Post by Joe_Bishop on 2009-09-28
> **andrewabc said:**
> Umm, will this change? I currently use 64 bit, and if it's not enabled it is yet another reason not to use 64 bit.

Have they even enabled [PGO](http://en.wikipedia.org/wiki/Profile-guided_optimization) yet that windows firefox has?
I think it's the reason not to use firefox. Don't support guys who don't respect you ;)

---

### Post by TrueTom on 2009-09-28
[http://ubuntuforums.org/showthread.php?t=1241797]("http://ubuntuforums.org/showthread.php?t=1241797")

---

