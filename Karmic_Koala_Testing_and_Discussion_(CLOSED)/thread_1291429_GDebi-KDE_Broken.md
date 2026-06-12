---
title: "GDebi-KDE Broken"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by captaincrook on 2009-10-14
Hello, testing Karmic for bug stuff and for fun stuff. All so far was ok, except a recent update broke my gdebi-kde package. Update from 10/13/09 I think. Anyways...

The output:

```
~$ gdebi-kde
Traceback (most recent call last):
  File "/usr/bin/gdebi-kde", line 32, in <module>
    from PyKDE4.kdecore import *
ImportError: No module named kdecore
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 100, in apport_excepthook
    os.O_WRONLY|os.O_CREAT|os.O_EXCL), 'w')
OSError: [Errno 13] Permission denied: '/var/crash/_usr_bin_gdebi-kde.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/gdebi-kde", line 32, in <module>
    from PyKDE4.kdecore import *
ImportError: No module named kdecore

```

Isolated incident or are others getting this? And is it possible to fix?

---

### Post by punchdrunkgrunt on 2009-10-15
Same here. Also jockey-kde and all other -kde apps give the same error message. It was working fine a couple of days ago. Seems to be a Python problem, might need to install or downgrade a Python package, but which one?

Damn you Karmic Koala! [shakes fist]

---

