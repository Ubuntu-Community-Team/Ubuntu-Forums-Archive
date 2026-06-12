---
title: "Error when downloading from software center"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by cotsy on 2010-12-07
Anytime i try and download something since i reinstalled ubuntu(dual booting with vista now, not sure if that makes a difference)i get this error from the software center,

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

The error details are as follows..

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 938, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

Any suggestions as to what the problem is?or how i might go about fixing it?

---

### Post by sikander3786 on 2010-12-08
Try this.

```
sudo apt-get install --reinstall app-install-data
```

And try to fire up Software Center again. If unsuccessul, post the output of this commands.

```
sudo apt-get update && sudo apt-get upgrade
```

---

