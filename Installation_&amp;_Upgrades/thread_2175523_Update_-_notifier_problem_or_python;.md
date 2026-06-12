---
title: "Update - notifier problem or python;"
date: 2013-09-19
forum: Installation &amp; Upgrades
---

### Post by mandu2 on 2013-09-19
Hi to all,

i am getting into the point.
When update-notifier starts, it goes minimized with an "x" as an icon. When i click on it i can read that "a problem occured while checking for the updates".
When i kill it and start it from console, no error appears. But when i click on "check for updates" on update-nofitier, then the following output appears on console:

```

Traceback (most recent call last):
  File "/usr/lib/update-notifier/backend_helper.py", line 3, in <module>
    import argparse
  File "/usr/lib/python2.7/argparse.py", line 92, in <module>
    from gettext import gettext as _
  File "/usr/lib/python2.7/gettext.py", line 49, in <module>
    import locale, copy, os, re, struct, sys
  File "/usr/lib/python2.7/locale.py", line 15, in <module>
    import encodings
ImportError: No module named encodings
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 66, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python2.7/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 18, in <module>
    import problem_report
  File "/usr/lib/python2.7/dist-packages/problem_report.py", line 15, in <module>
    from email.encoders import encode_base64
  File "/usr/lib/python2.7/email/__init__.py", line 118, in <module>
    import email.mime
ImportError: No module named mime

Original exception was:
Traceback (most recent call last):
  File "/usr/lib/update-notifier/backend_helper.py", line 3, in <module>
    import argparse
  File "/usr/lib/python2.7/argparse.py", line 92, in <module>
    from gettext import gettext as _
  File "/usr/lib/python2.7/gettext.py", line 49, in <module>
    import locale, copy, os, re, struct, sys
  File "/usr/lib/python2.7/locale.py", line 15, in <module>
    import encodings
ImportError: No module named encodings




```

By the way, i can update and upgrade without any errors and i have reconfigured python 2.7 packet.
Moreover, this issue, that might has to do with python in general, is affecting other applications that use python and therefore i can not start them.

Any ideas on that?

---

### Post by ubfan1 on 2013-09-20
Looking at :
  File "/usr/lib/python2.7/locale.py", line 15, in <module>
    import encodings
ImportError: No module named encodings

Looks like either you are missing part of the standard python install, or your reconfiguration was bad, and standard paths
to pick up imports are broken.  Try undoing the reconfigurations, or if that does not fix, purge and reinstall python from
the command line.

---

