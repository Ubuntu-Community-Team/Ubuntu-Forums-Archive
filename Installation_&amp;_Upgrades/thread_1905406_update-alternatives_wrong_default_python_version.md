---
title: "update-alternatives wrong default python version"
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by Cowloon on 2012-01-06
Hi,

Attempting to upgrade packages in ubuntu 10.04 I get the error message that I've read many posts about:

> ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6

If I run:

```
update-alternatives --config python
```

it displays:

```
There is only one alternative in link group python: /usr/bin/python2.6
Nothing to configure.
```

What can I do? I've also tried what seem like bad suggestions I've read many places, to replace the link manually. It just gets reset and I get the same error again.

---

### Post by Cowloon on 2012-01-06
I should have added /usr/bin/python links to /etc/alternatives/python links to /usr/bin/python2.6.

---

### Post by sulyi on 2013-01-24
Beware, this workaround ( i.e. update-alternatives ) messes with pyversions  (aka. /usr/share/python/pyversions.py) .

To debug the problem i've added the red words to the code.

```

    167         # consistency check
    168         try:
    169             debian_default = read_default('default-version')
    170         except ValueError:
    171             debian_default = "python2.6"
    172         if not _default_version in (debian_default, os.path.join('/usr/bin', debian_defau    172 lt)):
    173             raise ValueError, "/usr/bin/python [COLOR=Red]version (%s)[/COLOR] does not match the python def    173 ault version. It must be reset to point to %s" % [COLOR=Red](_default_version[/COLOR],debian_default[COLOR=Red])[/COLOR]

```Out put changed to:

```

$ pyversions --default
pyversions: /usr/bin/python version (/etc/alternatives/python) does not match the python default version. It must be reset to point to python2.7

```So, i've

```

# update-alternatives --remove-all python
#  ls /usr/bin/python
ls: cannot access /usr/bin/python: No such file or directory
# ln -s /usr/bin/python2.7 /usr/bin/python
# file /usr/bin/python
/usr/bin/python: symbolic link to `/usr/bin/python2.7'

```Fyi, i could fix the following error message with this.

```

Setting up python-gtk2-dev (2.24.0-3) ...
dpkg: error processing python-gtk2-dev (--configure):
 subprocess installed post-installation script returned error exit status 1

```Which was a huge mystery.

Anyway, update-alternatives is not a good solution to manage parallel  python versions. Because a chain of symbolic links apparently not followed by pyversions more than  one step or something. 

This was my best idea to fix this. Somebody please post a better one. 

Thanks.

---

### Post by sulyi on 2013-01-24
Also pyversion checks versions to

/usr/share/python/debian_defaults

file.

```

$ cat /usr/share/python/debian_defaults 
[DEFAULT]
# the default python version
default-version = python2.7

# all supported python versions
supported-versions = python2.7

# formerly supported python versions
old-versions = python2.3, python2.4, python2.5, python2.6

# unsupported versions, including older versions
unsupported-versions = python2.3, python2.4, python2.5, python2.6

```

---

