---
title: "/usr/include/uuid/uuid.h is missing"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2010-03-29
The file uuid/uuid.h is needed by a program I'm trying to compile (because there is no Ubuntu package for it).  I searched for that here and found one thread from 2007 that suggested it was part of the e2fsprogs package:

[http://ubuntuforums.org/showthread.php?t=343871&highlight=uuid.h](http://ubuntuforums.org/showthread.php?t=343871&highlight=uuid.h)

In Slackware, /usr/include/uuid/uuid.h is part of e2fsprogs there, too.  But in Ubuntu 9.10, e2fsprogs does not have that file at all.

So where did it go?  How do I get it?  Knowing what it is, I know it should be important to a few programs.  Is it in some other package, now?

---

### Post by srs5694 on 2010-03-29
You need to install a development/header package. In Ubuntu, this package is called uuid-dev.

---

### Post by Skaperen on 2010-03-29
> **srs5694 said:**
> You need to install a development/header package. In Ubuntu, this package is called uuid-dev.
Thanks, that got it!

I guess what I need now is a list of what files are provided in all Ubuntu packages ... without having to actually install every one of them and run "dpkg -L" or some equivalent on each .deb file (and avoid having do download them all).  I'll ask in another thread when I figure out which section is appropriate for that. I'm wanting to create a correlation index between various distributions that show the relationship of "what package do I install in distribution X to get all the stuff from package Y in distribution Z".

---

