---
title: "Never reinstalling Linux from scratch"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by debjit_bis08 on 2008-04-28
The question is simple I don't want to reinstall Ubuntu or any other distribution from scratch ever...

i.e I want to continue with my present installation but keep
upgrading the packages..

Is it too difficult ??

---

### Post by mannheim on 2008-04-28
I started with Ubuntu 5.04 (hoary) and upgraded 5.04 to 5.10 to 6.06 to 6.10 to 7.04 to 7.10 to 8.04, without ever reinstalling. This is supposed to just work; and for me, it has (pretty much).

---

### Post by debjit_bis08 on 2008-04-28
Wel what if I don't want to go the Ubuntu upgrade way

Ubuntu 7.10 had some problems on my laptop....
Is individual upgrade of packages possible.

i know there is the issue of dependencies 
but maybe there is some way out...

---

### Post by yyyc186 on 2008-04-28
Don't even remotely consider 8.04 if you don't want to install from scratch.

---

### Post by mannheim on 2008-04-30
> **debjit_bis08 said:**
> Wel what if I don't want to go the Ubuntu upgrade way

Ubuntu 7.10 had some problems on my laptop....
Is individual upgrade of packages possible.

i know there is the issue of dependencies 
but maybe there is some way out...

It isn't really feasible, because of the dependencies. If there is application or library in your present ubuntu installation that is causing problems, then it is sometimes possible to fix it by downloading the .deb file for the corresponding package in a newer version of ubuntu and installing that using dpkg. But most of the time, this will fail because of dependencies, or it will appear to succeed but cause something else to break. And in the long run it is next-to-impossible to maintain. Much better to stick with the ubuntu way.

Every time I have updgraded to the newer version, some bugs have been fixed and some others introduced; but the net gain has always been worth it. Always back up valuable data before upgrading, and be prepared for the possibility that you will have to reinstall: these forums show that bad things certainly happen to some people.

---

