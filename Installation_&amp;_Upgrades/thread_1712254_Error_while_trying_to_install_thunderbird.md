---
title: "Error while trying to install thunderbird"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by BenLeveque on 2011-03-22
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 779, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 958, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the librsync1 package. This might mean you need to manually fix this package.

This is the error I keep getting, I have no idea how to fix it is, as I am an absolute beginner.
Also, sorry if i've posted this in the wrong place.

---

### Post by Dutch70 on 2011-03-22
Hello & welcome to UF

 Try using Synaptic Package Manager to install it. You'll find synaptic under system > admin > synaptic.

If you have broken packages. Click the "edit" button in the menu bar & select "fix broken packages"

---

