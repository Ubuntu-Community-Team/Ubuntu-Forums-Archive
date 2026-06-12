---
title: "mod_mono"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by Digital221 on 2006-10-05
Hi all, hope you can help me on the one. Im trying to install mod_mono but its keeps installing for Apache 1.3 how can I force it to install for Apache2?  Below is what i am doing. I have allready installed mono and xsp. thanks :)

cd /tmp
wget [http://go-mono.com/sources/mod_mono/....1.13.5.tar.gz](http://go-mono.com/sources/mod_mono/....1.13.5.tar.gz)

tar xzf mod_mono-1.1.13.5.tar.gz
cd mod_mono-1.1.13.5
./configure --prefix=/usr
make
make install

---

