---
title: "Cannot install any softwares from ubuntu software center"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by Aditha on 2011-05-10
i just installed Ubuntu 11.04 and i'm new to Linux i tried to install few software from software center and i can't download or install any of the listed software... 
i even tried to open synaptic package manager and i couldn't open the same error keeps pooping up again and again 

attached the images of the error that come and below is the detail of the error


{  Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 926, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1046, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.   }


Thank you in advance

---

### Post by zvacet on 2011-05-11
Like the second message said be sure that you have all other installing programs (synaptic,update manager,apt-get from terminal) closed.Under synaptic>repositories> check all under ubuntu software (except the source & CD rom) and under updates check first two.Reload.In terminal

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

---

