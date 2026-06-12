---
title: "deluge not starting"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by ssc351 on 2007-12-27
Hi everyone, 

I'm running gusty with 0.5.8RC2 deluge, I installed it from the .deb...i had deluge running fine on fiesty but haven't used it since the upgrade,  i tried uninstalling everything and reinstalling and also tried removing the config files as some threads have suggested.  Here is the output from terminal:

Traceback (most recent call last):
  File "/usr/bin/deluge", line 44, in <module>
    import deluge.core
  File "/usr/lib/python2.5/site-packages/deluge/core.py", line 58, in <module>
    import deluge_core
ImportError: libboost_filesystem-gcc-mt-1_33_1.so.1.33.1: cannot open shared object file: No such file or director

---

### Post by ssc351 on 2007-12-28
bump

---

