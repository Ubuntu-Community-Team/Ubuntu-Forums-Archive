---
title: "fusion-icon still unavailable"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dentaku65 on 2009-03-14
Launching fusion-icon from the console, I get:
```
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.6/dist-packages/FusionIcon/interface.py", line 21, in <module>
    from util import env
  File "/usr/lib/python2.6/dist-packages/FusionIcon/util.py", line 21, in <module>
    import os, compizconfig, ConfigParser, time
ImportError: /usr/lib/python2.6/dist-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions

```
I think this as something to do with python upgrade of some weeks ago.

---

### Post by Ng Oon-Ee on 2009-03-14
Need more details on your system. I'm on 32-bit, all updates applied, and fusion-icon works fine here.

I remember one partial update screwing compiz up, including uninstalling fusion-icon. You may want to try removing it and all compiz-related stuff, then reinstalling (purge first).

---

### Post by dentaku65 on 2009-03-14
> **Ng Oon-Ee said:**
> Need more details on your system. I'm on 32-bit, all updates applied, and fusion-icon works fine here.

I remember one partial update screwing compiz up, including uninstalling fusion-icon. You may want to try removing it and all compiz-related stuff, then reinstalling (purge first).

I did it, but the problem persist.
Compiz works fine except for fusion-icon.
I'm 32-bit too. Which details you need of my system?

Thx

---

### Post by Ng Oon-Ee on 2009-03-14
I'm not rightly sure, really, as I don't know what exactly compiz interacts with. If compiz works fine, then your GC should be alright. Could it be a settings problem? (Create a new user to check that out). Otherwise, you should submit a bug report so those who really do know can help.

---

