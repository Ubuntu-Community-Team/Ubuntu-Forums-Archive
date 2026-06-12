---
title: "cant install packages"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by mastodon88 on 2010-05-19
hey all, i just switched from KDE to GNOME Ubuntu, 
i understand basically how to use package managers and such but for some reason i cannot install anything
this is the error:

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 126, in _process_transaction
    self.install_packages(self.trans.packages[0])
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 207, in install_packages
    self._commit_changes()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 551, in _commit_changes
    changes = self._cache.get_changes()
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 179, in get_changes
    for pkg in self:
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 161, in __iter__
    yield self[pkgname]
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 154, in __getitem__
    pkg = self._weakref[key] = Package(self, self._cache[key])
KeyError: 'kipi-0lugins-doc'


any help would be appreciated

---

