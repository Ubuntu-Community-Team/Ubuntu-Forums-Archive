---
title: "How to install Audacious"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by wersdaluv on 2007-01-01
I tried to install Audacious by running the ./configure file in the terminal and it stated this in the end:

Configuration:

  Install path:                           /usr/local
  Configuration path:                     $HOME/.audacious

  Use one plugin dir:                     no
  Allow user plugin dir:                  yes

  GNOME support
  -------------
  GConf support                           no


After the installation, I was expecting to see Audacious under the Sound and Video menu. It wasn't there so I tried the Debian menu and it still was not there. 

Did I install it correctly?

If I did, how do I run Audacious?

---

### Post by meng on 2007-01-01
alt-f2
audacious

---

### Post by wersdaluv on 2007-01-01
I tried it but the window just said, "The location or file could not be found."

What do I do? Did I not install it properly?

---

### Post by meng on 2007-01-01
Perhaps try:
sudo updatedb
locate audacious

---

### Post by nenolod on 2007-02-23
FFS, use our repository for Ubuntu.

---

