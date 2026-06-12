---
title: "How do you install .rpm and .tar.gz apps?"
date: 2005-08-15
forum: Installation &amp; Upgrades
---

### Post by SDutra on 2005-08-15
Basically what the title says: How do you install .rpm and .tar.gz apps? ty for any help.

Also I'm looking to buy a good reference book for Ubuntu Linux.  Any ideas that would be good for a first time user?

---

### Post by duminas on 2005-08-15
.tar.gz files are usually source.
file-roller (the default association for these), a GUI, can open them for you. From there, you can usually find a readme/install text file explaining what you need to do.

RPMs?
Use **alien -d filename**, and the RPM will be converted to a .deb.
Once it is a .deb, you just go **sudo dpkg -i filename.deb** (as in, the deb package version), and that should install it.
Such that, if you're trying to install my_application.rpm, you'd go **alien -d my_application.rpm** and then **sudo dpkg -i my_application.deb**--fairly simple.

About buying a book... you shouldn't need to.
Most issues can be figured out by looking at the wiki ([here](https://wiki.ubuntu.com/)), and the [Ubuntu Guide](http://www.ubuntuguide.org).

---

