---
title: "update-manager error -- python import"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by dkuhlman on 2013-02-11
When I try to run update-manager, I get this:

```
$ update-manager?
Traceback (most recent call last):?
  File "/usr/bin/update-manager", line 28, in <module>?
    from gi.repository import Gtk?
  File "/usr/lib/python3/dist-packages/gi/__init__.py", line 27, in <module>?
    from ._gi import _API, Repository?
ImportError: /usr/lib/python3/dist-packages/gi/_gi.cpython-32mu.so: undefined symbol: g_vfunc_info_invoke?

```

I tried doing:

```
$ sudo aptitude reinstall python3-gi
```

but that did not fix it.

I've also done:

```
$sudo aptitude update
$ sudo aptitude full-upgrade
```

Here is my /etc/lsb-release:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
```

I've tried several Web searches and several searches on Ubuntu Forums, but could not find anything that helped.

Thanks in advance for any suggestions.

- Dave

---

