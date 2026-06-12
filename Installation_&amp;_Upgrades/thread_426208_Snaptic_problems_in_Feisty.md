---
title: "Snaptic problems in Feisty"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by ruz322 on 2007-04-28
I'm trying to install gtkpod but when i do:
sudo apt-get install gtkpod

I am met with an error saying my system has unmet dependencies and that I have broken packages. When I run synaptic and use the broken filter two show up:
libstdc++6-4.1-dev
libtool

I attempt to install these updates but get this error:

E: /cdrom//pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_i386.deb: trying to overwrite `/usr/lib/libanl.a', which is also in package glibc-devel


Please help!

---

### Post by bapoumba on 2007-04-28
gtkpod is in universe, do you have these repositories enabled?

---

### Post by ruz322 on 2007-04-28
yea, i do, but i dont think thats the problem. apt-get finds the package but it seems like i may have a corrupted cd that its trying to isntall that glibc package from. just wanted another opinion.

---

### Post by bapoumba on 2007-04-28
Hum, sorry, I read your post a little quickly...
Could you post your sources.list ? (**cat /etc/apt/sources.list**). You may still have the cdrom enabled.

---

