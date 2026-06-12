---
title: "Symlink fix doesn't work"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by eckscalibur on 2011-08-19
Hi, I'm trying to install bitpim on Ubuntu 11.04 and I run into this problem:

```
Traceback (most recent call last):
  File "/opt/cx_Freeze-3.0.3/initscripts/ConsoleSetLibPath.py", line 35, in <module>
  File "src/bp.py", line 20, in <module>
  File "src/bp_cli.py", line 21, in <module>
  File "src/bp_config.py", line 19, in <module>
  File "src/guihelper.py", line 23, in <module>
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/__init__.py", line 45, in <module>
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 4, in <module>
  File "ExtensionLoader_wx__core_.py", line 12, in <module>
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory
```

After finding a howto, I tried fixing it by making a symlink to libtiff.so.4, but the error message still shows whenever I run bitpim.  Any ideas?

EDIT:  I tried reinstalling libtiff4 and the dev package and redoing the symlink and it suddenly works now. *shrug*

---

