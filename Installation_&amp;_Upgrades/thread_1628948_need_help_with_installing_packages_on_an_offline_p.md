---
title: "need help with installing packages on an offline pc"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by gobis on 2010-11-23
Hello everyone,

I installed ubuntu 10.04 LTS on my home pc alongside windows 7. This being a pc without an internet connection, I thought I could use my dual-booting laptop to carry packages downloaded from internet repositories. I can transfer the packages from the laptop's cache, but then I need to find a method easier than installing them individually, while also taking care of dependencies. In the case of g++, circular dependencies made even that impossible.

Now, I know of aptoncd, but it seems to offer help only in recovering packages, not in installing them. It has the option of creating an installation cd, but after creating an iso on the laptop, and mounting it on the pc, I don't know what to do for installing them.

If anyone can provide me with some pointers, I can struggle easier, I think.

Best wishes for everyone,
Hurol Aslan

---

### Post by sikander3786 on 2010-11-23
Hi.

Please take a look here.

[http://keryxproject.org](http://keryxproject.org)

---

### Post by oldos2er on 2010-11-23
Gdebi (GUI) and dpkg (CLI) should both work, assuming you have all needed dependencies in one folder.

---

### Post by gobis on 2010-12-07
Hello again,

I have not had a chance to check for answers here for a long time, but I found the solution on one of the ubuntu community webpages. dpkg-dev turned out to be the answer. It helps construct an installable package list based on another existing and updated ubuntu installation. That way, I was able to install packages I selected from the laptop to my offline pc.

Thanks everyone for helpful hints.
Hurol

---

