---
title: "How to install xbmc"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by KuroYoma on 2008-07-02
How do i install xbmc_2.1a2.orig.tar.gz?  any help is appreciated.

---

### Post by Partyboi2 on 2008-07-02
You can install it this way, unless you are wanting  compiling experience  :)
Add to /etc/apt/sources.list (System>Admin>Software Sources>Third Party Software)

```
deb [http://ppa.launchpad.net/team-xbmc-hardy/ubuntu](http://ppa.launchpad.net/team-xbmc-hardy/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/team-xbmc-hardy/ubuntu](http://ppa.launchpad.net/team-xbmc-hardy/ubuntu) hardy main
```then close Software Sources and open a terminal and install by
```
sudo apt-get install xbmc xbmc-skin-* xbmc-eventclients-*
```

---

### Post by KuroYoma on 2008-07-02
Thank you very much.

---

