---
title: "[SOLVED] Why do unofficial repo's cause errors when upgrading?"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by MalfunctioningMartian on 2007-10-15
Why do unofficial repo's cause errors when upgrading? I'm curious.

---

### Post by Soybean on 2007-10-15
What sort of errors?

It's probably got to do with the authentication features... if so, you can fix it if you can find the unofficial repository's key, along with instructions for setting it up. I would try to explain it in more detail, but it's one of those things where I understand the concept but forget all the correct terminology. :oops:

---

### Post by mjwood0 on 2007-10-15
First, a little background...

A distro (in Linux speak) is basically a set of programs, kernel and libraries which work particularly well together.  What this means for a developer is that you have the correct versions of libraries to go with the correct version of compilers which go with the correct version of applications.

If you upgrade the libraries for instance, you may find that many of the applications won't compile correctly.  As much as we'd like things to be backward compatible, it just doesn't always happen.

So... to your point.  If you have unofficial repos enabled, and that repo contains a newer version of something, you can cause dependency problems and end up with things that are either too new, too old or simply don't have the correct parameters during compile time to play nicely with the rest of the distro.  (Yes, some things are tweaked to get them happily playing with the rest of the distro.  Therefore, there is a minimal set of non-standard items in a specific distro).

Hope this helps!

---

### Post by bapoumba on 2007-10-15
Moved to "Installation & Upgrades".

---

### Post by MalfunctioningMartian on 2007-10-15
Thanks a lot. I understand much better now.

---

