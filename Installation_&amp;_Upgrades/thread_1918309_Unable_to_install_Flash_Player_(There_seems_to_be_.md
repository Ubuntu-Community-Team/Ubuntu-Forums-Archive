---
title: "Unable to install Flash Player (There seems to be a programming error in aptdaemon)"
date: 2012-01-31
forum: Installation &amp; Upgrades
---

### Post by zbzikowany on 2012-01-31
An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Details >

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


Am new to ubuntu, just installed, help would be appreciated :) Ty guys.

---

### Post by jcroyle on 2012-01-31
have you tried reinstalling aptdaemon go to synaptic package manager type in aptdaemon in the search box then right click the package and mark for reinstallation or you could   

sudo apt-get --reinstall install aptdeamon

also it looks like you have a small dependency problem 
which player are you installing

---

