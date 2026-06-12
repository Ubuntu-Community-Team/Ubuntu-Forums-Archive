---
title: "best moment to rsync local mirror from official repository"
date: 2013-09-17
forum: Installation &amp; Upgrades
---

### Post by grozours on 2013-09-17
Hello,

I have a local repository for my desktop platforms and for my ubuntu desktop generation ( pxe ).

I rsync 1 time per day, it appears that quite often that an update happens when i'm already making an rsync of the distant repository.
After that, i get a partial updated local mirror, breaking the dependencies of some packages, and breaking the pxe boot of my ubuntu desktop generation.

Is there a better day of the week to rsync an official repository in order to be sure to have a fully functionnal local repository.

Thanks in advance.

---

### Post by TheFu on 2013-09-17
So, you are mirroring everything in the canonical ubuntu repos?

Have you considered setting up **apt-cache-ng** instead for local needs?  It will be more efficient and you won't mirror anything that isn't actually used locally.

Of course, there are other uses for the mirror.

---

### Post by grozours on 2013-09-17
See my post here :
[http://ubuntuforums.org/showthread.php?t=1961393](http://ubuntuforums.org/showthread.php?t=1961393)

I only synchronise Ubuntu 12.04 with debmirror and some packages for pxe.
I don't synchronise the full repository.

---

