---
title: "stardict not only package list"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by weekendli on 2007-02-03
I can't find stardict on the ubuntu edgy packages list anymore, But I still can find it under  [here]("http://packages.ubuntulinux.org/feisty/utils/stardict") [ubuntulinux.org]

Here is my source list, do you know what's wrong with it, thank you.


deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

---

### Post by taurus on 2007-02-03
Looks like you need more sources for your /etc/apt/sources.list.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

