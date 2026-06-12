---
title: "hellanzb won't start?"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by heiNey on 2010-03-31
i'm not sure if this is the right place to put this, but im running lucid lynx beta and tried installing/running hellanzb and im getting this error when starting the daemon:

```

hellanzb -D
/usr/lib/python2.6/dist-packages/twisted/internet/default.py:15: DeprecationWarning: twisted.internet.default is deprecated. Use posixbase or selectreactor instead.
  warnings.warn("twisted.internet.default is deprecated. Use posixbase or selectreactor instead.", category=DeprecationWarning)
Traceback (most recent call last):
  File "/usr/bin/hellanzb", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/pymodules/python2.6/Hellanzb/Core.py", line 9, in <module>
    from Hellanzb.HellaReactor import HellaReactor
  File "/usr/lib/pymodules/python2.6/Hellanzb/HellaReactor.py", line 18, in <module>
    from twisted.internet.default import _NO_FILENO
ImportError: cannot import name _NO_FILENO

```

have no idea how to fix it.  i googled for a bit and found some patches, but i dont know how to use them.  can someone help?

---

