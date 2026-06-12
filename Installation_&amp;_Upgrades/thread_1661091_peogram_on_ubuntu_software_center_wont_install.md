---
title: "peogram on ubuntu software center wont install"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by hJ1ub5V4 on 2011-01-06
what ever program i try to download it displays this....what should i do???:confused::confused::confused:

.........this is the whole error thing



   An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

details

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 769, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 948, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the libgimp2.0 package. This might mean you need to manually fix this package.

---

### Post by hJ1ub5V4 on 2011-01-06
:lolflag: no, i solved it my self,sorry...bye!!!!:lolflag::guitar:

---

### Post by 1chess2u Christian on 2011-01-06
waiiiit!!!!!! How did you fix it? I am getting the same message!

---

### Post by claire14 on 2011-02-14
hi i get the same message how did you fix it

---

