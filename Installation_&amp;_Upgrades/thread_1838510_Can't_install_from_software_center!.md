---
title: "Can't install from software center!"
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by thecompgame on 2011-09-03
I keep getting this error when i try to install something from the software center...
An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.
> 
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


---

### Post by pierreyy on 2011-09-03
hey 

  try reinstalling the software center 

 if i remember correctly :

>  apt-get install software-center

  btw the command might be wrong...im working off of what little memory i already have :P let me know what happens

---

