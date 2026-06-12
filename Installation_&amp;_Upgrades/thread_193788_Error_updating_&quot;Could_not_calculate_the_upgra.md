---
title: "Error updating: &quot;Could not calculate the upgrade&quot;"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by miceagol on 2006-06-10
When I run the update manager to update from Breezy Badger to Dapper Drake I get the following error while the upgrade tool is "Downloading and installing the upgrades":
> 
Could not calculate the upgrade
A unresolvable problem occured while calculating the upgrade. Please report this as a bug.


Does anybody know the cause of this error? :( :confused: 

I get no error messages in the terminal when this error window pops up, but this was my output when the update program was running:
```

michaeka@laptop:~$ gksudo "update-manager"
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
/usr/lib/python2.4/site-packages/UpdateManager/MetaRelease.py:171: DeprecationWarning: Class MetaRelease is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
  gobject.type_register(MetaRelease)
extracting '/tmp/tmpbhfOXT/dapper.tar.gz'
authenticate '/tmp/tmpbhfOXT/dapper.tar.gz' against '/tmp/tmpbhfOXT/dapper.tar.gz.gpg'
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

```

---

### Post by miceagol on 2006-06-10
Please check [http://www.ubuntuforums.org/showthread.php?t=180411](http://www.ubuntuforums.org/showthread.php?t=180411) for a solution to this error.

---

