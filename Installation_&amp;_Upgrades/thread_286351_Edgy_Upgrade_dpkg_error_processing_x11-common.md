---
title: "Edgy Upgrade: dpkg error processing x11-common"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Schluppy on 2006-10-27
Hey folks, seems I've got a bit of a show stopper here.

While attempting the dist-upgrade using either aptitude or apt-get, the install fails with the following error:

```
Unpacking x11-common (from .../x11-common_1%3a7.1.1ubuntu6_i386.deb) ...
Replacing files in old package xinit ...
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/bin', which is also in package xli
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

Being a relative noob, I'm at a complete loss and google isn't helping much.

Is it a problem with the deb? Or could it be a conflict between x11-common and xli as the error suggests? If so, any idea how to work around it?

Any tips or ideas would be appreciated. Thanks!

---

### Post by Schluppy on 2006-10-28
Solved.

For anyone else running into similar issues, the problem appeared to be caused by having the universe repositories enabled - thus causing a conflict between xorg-common and xli.

The solution was simply "dpkg --purge xli" then starting the aptitude update process again.

---

### Post by greew on 2006-10-28
LOTS of kisses to you!! I had the exact same problem - except mine was with fglrx instead of xli - but using the dpkg --purge xli solved the problem!

Thanks a lot!

---

### Post by agger on 2006-11-20
> **Schluppy said:**
> Solved.

For anyone else running into similar issues, the problem appeared to be caused by having the universe repositories enabled - thus causing a conflict between xorg-common and xli.

The solution was simply "dpkg --purge xli" then starting the aptitude update process again.

Wow! I'm having the exact same problem myself - I'm going to try this out when I get home to my poor old Xubuntu box which can currently only boot into the TTYs!

thanks a lot,
Carsten

---

### Post by exhuma.twn on 2007-07-24
How did you figure out which package was conflicting?
I have the same problem, but simply purging xli did not help.
Did you disable the universe repos?
Did you do anything else?

I'm at a loss with this. :confused:

---

