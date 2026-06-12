---
title: "An unhandlable error occured."
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by dev_redant on 2011-05-29
*There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.*
Yes, I'm having this terrible problem. 
I just got Ubuntu today and it's been working great. But, when I tried to install Eclipse I got this error message. 
I tried hitting details and got this:

```
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-bin package. This might mean you need to manually fix this package.
```
I think it has something to do with my cancelled installation of Java, but I don't know how to fix it. 
Could anyone help me? I'm running Natty Narwhal (11.04) On an MSI WindTouch desktop computer. 
Thanks!
(I've tried looking around these forums but nothing has helped me..)
~RedAnt :confused:
THIS HAS BEEN SOLVED. -SoLvEd-

---

### Post by dev_redant on 2011-05-29
Nvm, I just had a friend figure out the problem for me.
:)

---

### Post by Markmental on 2011-05-29
> **dev_redant said:**
> Nvm, I just had a friend figure out the problem for me.
:)
what did he do to fix it?

---

