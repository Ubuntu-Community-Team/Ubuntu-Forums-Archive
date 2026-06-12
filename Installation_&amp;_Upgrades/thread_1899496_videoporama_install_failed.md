---
title: "videoporama install failed"
date: 2011-12-23
forum: Installation &amp; Upgrades
---

### Post by pierreu1 on 2011-12-23
Here is the code, after I installed videoporama in U, Software Center. Subsequently, I tried to install Audacity and I got the same result. I recently upgraded from 11.04 to 11.10:


Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

Any idea of what I should do?

---

