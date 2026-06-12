---
title: "mod_python doesnt work after recent python feisty update"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by gert cuykens on 2007-06-08
[Fri Jun 08 10:28:43 2007] [error] make_obcallback: could not call init.\n
AttributeError: init
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 44, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
AttributeError: 'module' object has no attribute 'argv'

Original exception was:
AttributeError: init
[Fri Jun 08 10:28:43 2007] [error] make_obcallback: mod_python version mismatch, expected '3.2.10', found '<unknown>'.
[Fri Jun 08 10:28:43 2007] [error] make_obcallback: mod_python modules location '/usr/lib/python2.5/site-packages/mod_python/__init__.pyc'.
[Fri Jun 08 10:28:43 2007] [error] python_handler: no interpreter callback found.
[Fri Jun 08 10:28:43 2007] [error] [client 192.168.1.101] python_handler: Can't get/create interpreter., referer: [http://192.168.1.17/trunk/static/forum/forum.htm](http://192.168.1.17/trunk/static/forum/forum.htm)

---

