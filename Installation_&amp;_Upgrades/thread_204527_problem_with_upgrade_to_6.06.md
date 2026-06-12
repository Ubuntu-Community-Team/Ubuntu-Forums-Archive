---
title: "problem with upgrade to 6.06"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by lucas_cz on 2006-06-27
Hello everyone!

I came accross a big problem while i was upgrading Ubuntu instalation from 5.10 to 6.06. 

I think this will explain the situation:
-----------------------------------------------------------------------------------------------------
lucas@lucas:~$ gksudo "update-manager"
  warnings.warn("apt API not stable yet", FutureWarning)
/usr/lib/python2.4/site-packages/UpdateManager/MetaRelease.py:171: DeprecationWarning: Class MetaRelease is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
  gobject.type_register(MetaRelease)
extracting '/tmp/tmpw25A5a/dapper.tar.gz'
authenticate '/tmp/tmpw25A5a/dapper.tar.gz' against '/tmp/tmpw25A5a/dapper.tar.gz.gpg'
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
-----------------------------------------------------------------------------------------------------

The upgrade failed.
Can anyone help me with solving this problem?

Thank you.

Best Regards!
Lukasz Czyzewski.

---

