---
title: "Funguloids won't install with Ubuntu Software Center"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by thedaemon on 2009-10-17
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 91, in _process_transaction
    self.install_packages(**self.trans.kwargs)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 155, in install_packages
    self._mark_packages_for_installation(package_names)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 178, in _mark_packages_for_installation
    pkg.markInstall()
  File "/usr/lib/python2.6/dist-packages/apt/package.py", line 1076, in markInstall
    fixer.Resolve(True)
SystemError: E:Unable to correct problems, you have held broken packages.



That's the error message, any ideas? Seems like python is muffed?

---

### Post by inportb on 2009-10-17
How do you know that Ubuntu Software Center is at fault? Have you tried installing using Synaptic, aptitude, or apt-get?

---

