---
title: "apt daemon"
date: 2012-02-10
forum: Installation &amp; Upgrades
---

### Post by tyscifi on 2012-02-10
when i try to install anything i get this error (from ubuntu app store) There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. 
details

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package.

---

### Post by cortman on 2012-02-10
> **tyscifi said:**
> when i try to install anything i get this error (from ubuntu app store) There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. 
details

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package.

Have you tried running

```
sudo apt-get install -f
```

to fix broken packages?

---

### Post by tyscifi on 2012-02-11
when i do every thing  is fine but then i get a agreement screen from sun java 6 from when i tryed to install that and it has this at the end <ok> but clicking and pressing enter does nothing

---

### Post by cortman on 2012-02-11
Try uninstalling and reinstalling-

```
sudo apt-get purge default-jre
sudo apt-get install default jre
```

Did you run the command I gave previously?

---

