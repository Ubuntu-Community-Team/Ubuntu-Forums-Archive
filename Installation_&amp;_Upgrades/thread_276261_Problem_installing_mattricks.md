---
title: "Problem installing mattricks"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by 3zero2 on 2006-10-12
Hi all,

I'm trying to install a program called Mattricks ([http://www.lysator.liu.se/mattricks/](http://www.lysator.liu.se/mattricks/)) on Edgy. I downloaded the .deb package which should make things easier but I'm getting an error:

Error: Dependency is not satisfiable: python

When trying to install from terminal I get this error:

```
Selecting previously deselected package mattricks.
(Reading database ... 97975 files and directories currently installed.)
Unpacking mattricks (from .../mattricks_0.7-1_all.deb) ...
dpkg: dependency problems prevent configuration of mattricks:
 mattricks depends on python (<< 2.4); however:
  Version of python on system is 2.4.3-11ubuntu3.
 mattricks depends on libwxgtk2.4-python; however:
  Package libwxgtk2.4-python is not installed.
dpkg: error processing mattricks (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mattricks

```

Is there anything i can do to solve this problem?

thanks

---

