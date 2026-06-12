---
title: "Finding packages that are not on an LTS point release CD, that work with that CD"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by venzy on 2010-03-17
Hello,

A while ago I posted this thread, with no responses:
[http://ubuntuforums.org/showthread.php?t=1057817](http://ubuntuforums.org/showthread.php?t=1057817)

So I'll try a different tack in the hope that someone can help.

I deploy into an environment that for "security" reasons cannot be kept up to date with wherever the ubuntu archive is up to (with awareness that this is avoiding security updates...).  It is a sealed system not connected to the internet.

I'm working with the 8.04.1 LTS, and my customer is in an 'if it ain't broke don't change it' frame of mind w.r.t. moving to 8.04.4.  My main problem comes in two variations:
1. Some packages my runtime system depends on are not distributed on the 8.04.1 DVD, but were available in the full ubuntu archive at the time of the point release (and still are, in an up-to-date form).  My concern is that if I take the 8.04.4-ish version of a package it will not work correctly with an otherwise 8.04.1 system.  In general I am expecting that it *might*, and the versioned dependencies it has on other packages will be loose enough.
2. Some packages my build system (which produces what I put onto the runtime system) depend on are also not on the DVD.  So almost a repeat of 1 above, except that I am generally running afoul of strictly-versioned dependencies (the -dev version of a lib package depends on the matching lib package having exactly the same version).  If the non-dev lib package is on the DVD, but is not the same version as the -dev package I have from an archive mirror taken just before the 8.04.1 release, I believe I'm screwed?

So my two questions are:
a. Is there such a thing as a copy of the full ubuntu archive taken at the exact time the 8.04.1 LTS was released?  I think that would solve most of my problems.
b. Any other suggestions?

Thanks in advance,
-Dave.

---

### Post by phillw on 2010-03-17
Hi,

if the system is behaving and has no contact with the internet - Leave it in peace :D

8.04.1 --> 8.04.4 wouldn't break anything and can be done via an 'alternate install CD', so there would be no need to connect to the internet.

8.04.4 is released to ready the LTS of 8.04 for the next LTS 10.04. 8.04 will be supported for another 12 months anyway, but none of this matters if you're not applying security patches etc.

There is a a great deal of wisdom in the saying "If it ain't broke, don't fix it". As the flip side of that is "If it ain't broke, you haven't tweaked it enough".

So, with no internet connection, I'd leave a happy system just as that - a happy system. 
If it is becoming a problem for you to maintain, then 8.04.4 would be a good move for you and the customer's machine. If you wish to be ultra cautious, take a 'snap-shot' of the existing system onto a hard drive and apply the 8.04.4 update to it.

Regards,

Phill.

---

