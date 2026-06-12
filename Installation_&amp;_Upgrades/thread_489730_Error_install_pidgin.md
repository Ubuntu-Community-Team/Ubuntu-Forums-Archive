---
title: "Error install pidgin"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by mzar on 2007-07-01
Hi,

I'm using Ubuntu Feisty. After doing build-essential, because dont have compiler i got this error.

```
#
he msgfmt command is required to build libpurple.  If it is installed
#
on your system, ensure that it is in your path.  If it is not, install
#
GNU gettext to continue. 
```

How to solve it?

---

### Post by Mapkoz on 2007-07-01
have you tried to install these 2 libraries?
```
sudo apt-get install msgfmt
```
and 
```
sudo apt-get install GNU gettext
``` (or maybe only 'gettext')

are you installing it from source code or from a .deb file?

---

### Post by mzar on 2007-07-01
Install from source code. All solve.

Thank!

---

### Post by Neatchee on 2007-07-14
Michael Trausch and I have been working on backports of Pidgin for Feisty.  He does the 32bit backports, I do the 64bit backports.  These include both the base pidgin install, as well as working ports of Guifications and OTR (Off the Record messaging).

For an easier time of it, and to prevent problems that can occur if you later have to change your install (no uninstall with source!), you can download our deb packages here:  [http://www.trausch.us/pidgin](http://www.trausch.us/pidgin)

Enjoy!

---

