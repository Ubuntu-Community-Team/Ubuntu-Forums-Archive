---
title: "Trying to upgrade beryl, python2.5-minimal is BROKEN.  HELP!!!"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by meldroc on 2007-01-28
OK, here's the log when I try to reinstall beryl on my edgy eft machine...

```
meldroc@silverfish:~$ sudo apt-get install beryl
Reading package lists... Done
Building dependency tree
Reading state information... Done
beryl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up python2.5-minimal (2.5-2ubuntu2) ...
Linking and byte-compiling packages for runtime python2.5...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 984, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 537, in read_version_info
    self.version_info = pyversions.parse_versions(self.version_field)
  File "/usr/share/pycentral-data/pyversions.py", line 41, in parse_versions
    raise ValueError, 'error parsing Python-Version attribute'
ValueError: error parsing Python-Version attribute
dpkg: error processing python2.5-minimal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.5:
 python2.5 depends on python2.5-minimal (= 2.5-2ubuntu2); however:
  Package python2.5-minimal is not configured yet.
dpkg: error processing python2.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of beryl-settings-bindings:
 beryl-settings-bindings depends on python (>= 2.5) | python2.5; however:
  Version of python on system is 2.4.3-11ubuntu3.
  Package python2.5 is not configured yet.
dpkg: error processing beryl-settings-bindings (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of beryl-settings:
 beryl-settings depends on beryl-settings-bindings; however:
  Package beryl-settings-bindings is not configured yet.
dpkg: error processing beryl-settings (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of beryl:
 beryl depends on beryl-settings; however:
  Package beryl-settings is not configured yet.
dpkg: error processing beryl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of beryl-manager:
 beryl-manager depends on beryl; however:
  Package beryl is not configured yet.
dpkg: error processing beryl-manager (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.5-minimal
 python2.5
 beryl-settings-bindings
 beryl-settings
 beryl
 beryl-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)
meldroc@silverfish:~$
```

How do I fix this?

---

