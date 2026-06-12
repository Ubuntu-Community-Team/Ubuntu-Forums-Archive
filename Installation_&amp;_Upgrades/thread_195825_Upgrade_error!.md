---
title: "Upgrade error!"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by mattlach on 2006-06-13
If I run the upgrade manager I and select to upgrade it downloads the "upgrade tool" and when it completes it quits.

If I run GKSUDO the terminal states the following:

```

matt@matt:~$ gksudo update-manager
warnings.warn("apt API not stable yet", FutureWarning)
/usr/lib/python2.4/site-packages/UpdateManager/MetaRelease.py:171: DeprecationWarning: Class MetaRelease is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
gobject.type_register(MetaRelease)
extracting '/tmp/tmpw5fQ_q/dapper.tar.gz'
authenticate '/tmp/tmpw5fQ_q/dapper.tar.gz' against '/tmp/tmpw5fQ_q/dapper.tar.gz.gpg'
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
warnings.warn("apt API not stable yet", FutureWarning)
can't find DistUpgradeViewGtk

```


I'm thinking this can probably be solved by reinstalling whatever package "DistUpgradeViewGtk" is a part of, but I have no idea what that migh be.

Any ideas?

Thanks,
Matt

---

### Post by rbalfour on 2006-06-13
Have you tried removing the update-manager and reinstalling?

$ apt-get remove update-manager

then after that's done.

$ apt-get install update-manager

---

### Post by mattlach on 2006-06-13
[QUOTE=rbalfour]Have you tried removing the update-manager and reinstalling?

$ apt-get remove update-manager

then after that's done.

$ apt-get install update-manager[/QUOTE]

I used synaptic to "reinstall" it, but I never tried removing and reinstalling it.

I'll give that a shot tonight.

---

### Post by wiertel on 2006-09-07
I had the same problem when trying to upgrade my Dapper to Egdy.

```
root@kimiko:~ # update-manager -c -d
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
extracting '/tmp/tmp4B84_A/edgy.tar.gz'
authenticate '/tmp/tmp4B84_A/edgy.tar.gz' against '/tmp/tmp4B84_A/edgy.tar.gz.gpg'
can't find DistUpgradeViewGtk
```

For me the solution was
```
# apt-get install python-vte
```

---

### Post by senectus on 2006-10-29
Yeah that fixed it for me as well, thanks.

---

