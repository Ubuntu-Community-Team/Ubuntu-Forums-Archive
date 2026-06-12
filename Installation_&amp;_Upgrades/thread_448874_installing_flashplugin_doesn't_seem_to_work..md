---
title: "installing flashplugin doesn't seem to work."
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by trunks14 on 2007-05-19
i've just installed ubuntu and want to install the macromedia flash plugin for firefox, here's what i do:


-Download the flash plugin (.rpm) from the macromedia website
-sudo apt-get update
-sudo apt-get install alien
-sudo alien (flash .rpm)
-sudo dpkg -i (flash .deb)

If then i double click the .deb package ubuntu informs that flashplugin is already installed, but i can't see flash objects in firefox.

---

### Post by taurus on 2007-05-19
Why even bother with the .rpm version.  Remove it with 

```
sudo dpkg -r **filename**
```
and use this guide to install it.

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

