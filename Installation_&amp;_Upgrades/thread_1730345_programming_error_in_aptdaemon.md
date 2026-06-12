---
title: "programming error in aptdaemon"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by skymonster93 on 2011-04-15
hey guys,

i saw a guy posted something about a programming error when he tried to install WINE software, however this happened when i tried to install Skype and flash player this morning (more importantly Skype)

it says: There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other tasks related to package management. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

DETAILS >
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the libaudio2 package. This might mean you need to manually fix this package.



can someone please help?? Im in desparate need for skype on Ubuntu and i am relatively new to Ubuntu and they way you install files on it...
(Yes I am a Windows and Mac man.....) 


Yours hopefully,

SkyMonster

---

