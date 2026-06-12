---
title: "failed updates"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by php_penguin on 2008-03-21
Hi there ... might as well post this before the inevitable flurry of "how do I upgrade to 8.04" stuff :D

Usually for me, updates run fine and just do it ... but a few days ago I had a fresh batch of updates, and they are refusing to install...

It seems to me that when an update fails, and you click retry, it just re-attempts from the same package... short of actually doing "apt-get clean" and so on, it's damn hard to make it get past that stage of "just retry pointlessly".... 

perhaps some sort of system for checking for repeated failures (maybe, more than 3 failures) and then completely purging the package files and any stored info about that file, effectively resynching with the server...

or am I missing sometihng?

btw the package is mysql-server-5.0, although for a while it was holding up a bunch of other ones too.

---

