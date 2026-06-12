---
title: "Error - Ubuntu Software Center"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by zzytds on 2010-12-17
Whenever I try to istall an app with USC I get the error below:

An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

Details:


Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 938, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the scilab-data package. This might mean you need to manually fix this package.


How can I fix it?

---

### Post by Rubi1200 on 2010-12-17
Hi and welcome to the forums :)

Go to Applications > Accessories > Terminal and run the following commands.

```
sudo apt-get install -f

sudo dpkg --configure -a

sudo apt-get update
```

Run each command separately and report back if there are errors.

---

