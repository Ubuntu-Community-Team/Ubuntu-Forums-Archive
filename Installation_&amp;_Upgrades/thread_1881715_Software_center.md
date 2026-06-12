---
title: "Software center"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by Alan5901 on 2011-11-16
When ever I try to download a file I get the error bellow. 
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the unrar package. This might mean you need to manually fix this package.

Thanks for your help.

---

### Post by raja.genupula on 2011-11-16
go to synaptic search for** unrar **mark it upgrade and click apply .

and try to launch again.

if not done then try this

```
sudo apt-get clean all
sudo apt-get update
```

all the best

---

