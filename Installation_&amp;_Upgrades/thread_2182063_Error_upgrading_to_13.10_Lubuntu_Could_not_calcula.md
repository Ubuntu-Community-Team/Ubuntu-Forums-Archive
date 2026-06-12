---
title: "Error upgrading to 13.10 Lubuntu Could not calculate the upgrade?"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by LYJ7trm on 2013-10-20
After running sudo do-release-upgrade I get this error:



Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. 

What can I do?  Thanks

---

### Post by abrianb on 2013-10-20
Have you enabled non Ubuntu repositories by adding PPAs? This can cause this error. Just disable them and then install. You can add them back later.

---

### Post by kansasnoob on 2013-10-20
Quite possibly this bug:

[https://bugs.launchpad.net/ubuntu/saucy/+source/ubuntu-release-upgrader/+bug/1241123](https://bugs.launchpad.net/ubuntu/saucy/+source/ubuntu-release-upgrader/+bug/1241123)

According to comment #12:

> If you try upgrading use the dist-upgrader in -proposed by using do-
release-upgrade -p or update-manager -p, you should be able to upgrade
to Saucy.

But I've not personally tried it :)

---

### Post by LYJ7trm on 2013-11-12
Using sudo update-manager -p I get these errors:


ERROR:root:Could not find any typelib for Dbusmenu
ERROR:root:Could not find any typelib for Unity
WARNING:root:can not import unity GI cannot import name Dbusmenu
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 114, in <module>
    app = UpdateManager(data_dir, options)
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 111, in __init__
    self.options and self.options.use_proposed)
  File "/usr/lib/python3/dist-packages/UpdateManager/MetaReleaseGObject.py", line 44, in __init__
    MetaReleaseCore.__init__(self, useDevelopmentRelease, useProposed)
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 90, in __init__
    self.flavor_name = get_ubuntu_flavor_name()
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 447, in get_ubuntu_flavor_name
    pkg = get_ubuntu_flavor_package(cache=cache)
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 437, in get_ubuntu_flavor_package
    cache = apt.Cache()
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 105, in __init__
    self.open(progress)
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 151, in open
    self._depcache = apt_pkg.DepCache(self._cache)
SystemError: E:The package linux-headers-3.8.0-30 needs to be reinstalled, but I can't find an archive for it.





Similar results with  do-release-upgrade



Checking for a new Ubuntu release
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 111, in <module>
    useProposed=options.proposed_release)
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 90, in __init__
    self.flavor_name = get_ubuntu_flavor_name()
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 447, in get_ubuntu_flavor_name
    pkg = get_ubuntu_flavor_package(cache=cache)
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 437, in get_ubuntu_flavor_package
    cache = apt.Cache()
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 105, in __init__
    self.open(progress)
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 151, in open
    self._depcache = apt_pkg.DepCache(self._cache)
SystemError: E:The package linux-headers-3.8.0-30 needs to be reinstalled, but I can't find an archive for it.

---

