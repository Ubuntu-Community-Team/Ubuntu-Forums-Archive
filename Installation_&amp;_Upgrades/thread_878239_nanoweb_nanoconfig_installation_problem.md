---
title: "nanoweb nanoconfig installation problem"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by strider22 on 2008-08-02
In ubuntu 8.04 I installed nanoweb and nanoweb-nanoconfig using synaptic.
Nanoweb worked fine but nanoconfig did not.
I had to move the install directory and adjust permissions

cd /usr/share
mv nanoweb-nanoconfig nanoweb/defaultroot/nanoconfig
cd nanoweb/defaultroot/nanoconfig
sudo chmod +x *

I had already adjusted permissions on etc/nanoweb to +rw as specified for nanoconfig to have access.

---

