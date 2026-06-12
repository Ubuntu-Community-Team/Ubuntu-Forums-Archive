---
title: "Error running update-manager (12.04)"
date: 2014-02-13
forum: Installation &amp; Upgrades
---

### Post by Markus_Wiederkehr on 2014-02-13
When I start update-manager I see the error below. I tried *apt-get update && apt-get upgrade* but that did not help. Also tried to *apt-get install --reinstall* update-manager, aptdeamon, aptdeamon-data and python2.7.

Any ideas?

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

$ update-manager 
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 115, in <module>
    app = UpdateManager(data_dir, options)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 280, in __init__
    self.install_backend = backend.get_backend(self.window_main)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/backend/__init__.py", line 48, in get_backend
    from InstallBackendAptdaemon import InstallBackendAptdaemon
  File "/usr/lib/python2.7/dist-packages/UpdateManager/backend/InstallBackendAptdaemon.py", line 5, in <module>
    from aptdaemon import client, errors
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 70, in <module>
    class MemoizedMixIn(MemoizedTransaction, GObject.GObjectMeta):
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 316, in __getattr__
    return getattr(self._introspection_module, name)
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 135, in __getattr__
    self.__name__, name))
AttributeError: 'gi.repository.GObject' object has no attribute 'GObjectMeta'

---

### Post by oldos2er on 2014-02-14
Try ```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by Markus_Wiederkehr on 2014-02-17
I have tried dist-upgrade, two probably unrelated packages were updated (nvidia-304 and nvidia-settings-304). Unfortunately the problem still persists. Any other ideas?

---

### Post by Markus_Wiederkehr on 2014-02-17
SOLVED: I had a couple of packages that were 'newer than version in archive', python-gi among those. I manually downgraded the packages and now update-manager is working again.

---

