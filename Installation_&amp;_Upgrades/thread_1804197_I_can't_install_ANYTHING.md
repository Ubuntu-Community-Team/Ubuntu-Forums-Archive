---
title: "I can't install ANYTHING"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by Partian on 2011-07-14
I added a code into terminal and restarted, then I tried to install Java and this came up.



'There seems to be a programming error in aptdaemon. This is the software that allows you to install/remove software and to perform other package management related tasks.'


[PHP]Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package.
[/PHP]

---

### Post by Mark Phelps on 2011-07-14
WHY are you using the terminal to install anything?

Using the Software Center, or even using Synaptic, is a lot easier and has less problems.

---

