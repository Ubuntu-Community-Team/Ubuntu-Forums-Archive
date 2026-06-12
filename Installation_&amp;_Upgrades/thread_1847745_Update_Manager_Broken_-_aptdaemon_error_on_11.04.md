---
title: "Update Manager Broken - aptdaemon error on 11.04"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by TonMoan on 2011-09-21
My update manager hasnt updated in months because of an error in the aptdaemon.

> Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:Method  has died unexpectedly!, E:Sub-process  returned an error code (100), E:Method /usr/lib/apt/methods/ did not start correctly


I dont know how to fix it.  I've tried starting in recovery mode and that didnt work.  I can install from synaptic and ubuntu software center but not update from update manager.  Please help.

---

### Post by TonMoan on 2011-09-21
I just discovered why I havent been able to update for months.  Its the google chrome web browser update that was the problem.  Every update worked without error when I unchecked chrome update.  It just so happens the chrome update is the one I wanted the most.  Google chrome browser update errors out on both synaptic and update manager(its not listed in ubuntu software center).  Nice going google.

---

### Post by TonMoan on 2011-09-21
I downloaded the deb from google and ran it, it popped up in ubuntu software center with an upgrade button and my chrome is now updated.  Problems solved.  Although, we may never know why googles chrome update didnt work from update manager or synaptic.

---

