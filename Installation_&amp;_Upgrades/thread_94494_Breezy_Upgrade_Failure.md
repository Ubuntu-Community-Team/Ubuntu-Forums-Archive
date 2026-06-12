---
title: "Breezy Upgrade Failure"
date: 2005-11-24
forum: Installation &amp; Upgrades
---

### Post by johncox on 2005-11-24
I'm upgrading at the moment and dpkg has just choked on
a package with this error:

dpkg: error processing /var/cache/apt/archive/python-wxversion_2.6.1.1ubuntu_all.deb (--unpack)

trying to overwrite `/usr/lib/python2.4/site-packages/wxversion.py`
which is also in package wxpython_2.5.3

dpkg-deb: subprocess paste killed by signal (Broken pipe)

Errors were encountered while processing:
/var/cache/apt/archive/python-wxversion_2.6.1.1ubuntu_all.deb

E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried apt-get install -f but get the same error

How should I deal this?
AFAIK I'm not dependant on wxpython so I don't mind uninstalling it
if that will fix the problem.  Can I do that half way through an upgrade
and what's the best way to go about it?

TIA

---

### Post by Xian on 2005-11-24
Simply remove the wxpython_2.5.3 package, proceed with the installation, and then reinstall the library afterwards if you require it on your system.

```
$ sudo apt-get remove wxpython2.5.3
$ sudo apt-get dist-upgrade
```

---

### Post by johncox on 2005-11-24
[QUOTE=Xian]Simply remove the wxpython_2.5.3 package, proceed with the installation, and then reinstall the library afterwards if you require it on your system.

```
$ sudo apt-get remove wxpython2.5.3
$ sudo apt-get dist-upgrade
```[/QUOTE]


Thanks Xian,

I tried this but it didnt work I just get another depenancy error

libwxgtk2.5.3-python: Depends: wxpython
python-wxgtk2.6: Depends python-wxversion but it is not going to be installed

So I remove python-wxgtk2.6 but

drpython: Depends: python-wxgtk2.6 but it is not going to be installed

And removing drpython gives

python-wxgtk2.6: Depends: python-wxversion

so I'm going round in circles :mad: 

Is there any way to break out of this loop???

---

### Post by Xian on 2005-11-24
[QUOTE=johncox]Is there any way to break out of this loop???[/QUOTE]
Issue these commands and then proceed with installation:

```
$ sudo dpkg -i --force-overwrite /var/cache/apt/archive/python-wxversion_2.6.1.1ubuntu_all.deb
$ sudo dpkg --configure -a
$ sudo apt-get -f install

```

---

