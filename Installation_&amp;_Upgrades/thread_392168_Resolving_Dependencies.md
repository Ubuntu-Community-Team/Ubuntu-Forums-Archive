---
title: "Resolving Dependencies"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by Aravind Kumar on 2007-03-24
When I tried to install yahoo messenger in Ubuntu using the following command

dpkg -i  ymessenger_1.0.4_1_i386.deb

it got some dependency errors. Is it possible to reslove the dependencies and install at the same time.

---

### Post by daynah on 2007-03-24
If it told you what packages it needed, I, being the lazy person I am and trying to learn the least linux commands except those that sneak through by mental difussion, would just "sudo aptitute install blah blah blah" those buggers. You can install many things at the same time using aptitute or apt-get, but I think it best to wait till after the dependences are all done before you try dpkg-ing.

sudo aptitute dependency1 dependency2 dependency3 

just copy and paste it, this only added one more command.

---

