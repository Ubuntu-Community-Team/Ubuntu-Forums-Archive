---
title: "Latex and Lyx repositories"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by st0nes on 2010-03-03
What do I have to add to source.list in 9.10 to be able to install laTeX and Lyx from the Ubuntu repositories?

---

### Post by r-senior on 2010-03-03
You need the universe repositories:

[http://packages.ubuntu.com/karmic/tex/]("http://packages.ubuntu.com/karmic/tex/")
[http://packages.ubuntu.com/karmic/lyx]("http://packages.ubuntu.com/karmic/lyx")

So this needs to be in /etc/apt/sources.list:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe

Or System -> Administration -> Software Sources, then click the "... (universe)" box.

---

### Post by st0nes on 2010-03-04
> **r-senior said:**
> You need the universe repositories:

[http://packages.ubuntu.com/karmic/tex/]("http://packages.ubuntu.com/karmic/tex/")
[http://packages.ubuntu.com/karmic/lyx]("http://packages.ubuntu.com/karmic/lyx")

So this needs to be in /etc/apt/sources.list:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe

Or System -> Administration -> Software Sources, then click the "... (universe)" box.

Thanks, but that doesn't help.  Added that line to source.list and ALL the boxes are ticked in software sources. I get:-
> LyX Document Processor
Not available in the current data

---

