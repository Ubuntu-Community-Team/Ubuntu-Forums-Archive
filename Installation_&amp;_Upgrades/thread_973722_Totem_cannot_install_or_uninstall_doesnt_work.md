---
title: "Totem cannot install or uninstall doesnt work"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by wilbur.harvey on 2008-11-07
Totem has gotten into a broken state.
It is not working, and I cannot install it, or uninstall it.

sudo dpkg -r totem-common
sudo: unable to resolve host whnmacpro
(Reading database ... 212143 files and directories currently installed.)
Removing totem-common ...
Warning: /usr/share/gconf/schemas/totem-handlers.schemas could not be found.
Warning: /usr/share/gconf/schemas/totem-video-thumbnail.schemas could not be found.
Warning: /usr/share/gconf/schemas/totem.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing totem-common (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 totem-common
wharvey@whnmacpro:~/Desktop$ 

Any ideas?

---

### Post by zvacet on 2008-11-07
> sudo: unable to resolve host whnmacpro

```
gksudo gedit /etc/hosts
```

and see if first two lines look like 

127.0.0.1 localhost
127.0.1.1 host

**Host=your host name**

---

