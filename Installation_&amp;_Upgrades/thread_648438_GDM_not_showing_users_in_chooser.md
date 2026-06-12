---
title: "GDM not showing users in chooser"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by domstyledesign on 2007-12-23
i just did a fresh install of edubuntu 7.10. there are three users on the system, but none of them show up in gdm's chooser.

/etc/gdm/gdm.conf is here
[http://paste.ubuntu-nl.org/49434/](http://paste.ubuntu-nl.org/49434/)

and /etc/gdm/gdm.conf-custom is here
[http://paste.ubuntu-nl.org/49435/](http://paste.ubuntu-nl.org/49435/)


any thoughts?

---

### Post by domstyledesign on 2007-12-23
Fixed:

add the line

Browser=1

to the section

[greeter]


in /etc/gdm/gdm.conf-custom

---

