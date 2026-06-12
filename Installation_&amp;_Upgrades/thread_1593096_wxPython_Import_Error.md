---
title: "wxPython Import Error"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by shm56 on 2010-10-11
I am working on Ubuntu Lucid and trying to implement GNU Radio.I have successfully installed all required stuff for the radio but I need wxPython for GUI that is not getting worked.

My Python 2.6 is located at /usr/lib.Following is the error statement:

Traceback (most recent call last):
  File "/home/sapan/wx1.py", line 2, in <module>
    import wx
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/__init__.py", line 45, in <module>
    from wx._core import *
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 14774, in <module>
    from _misc import *
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_misc.py", line 4, in <module>
    import _misc_
ImportError: /usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_misc_.so: symbol _ZN7wxSound6CreateEiPKh, version WXU_2.8 not defined in file libwx_gtk2u_adv-2.8.so.0 with link time reference

Please update me if it is solved.Thanks

Sapan

---

### Post by shm56 on 2010-10-14
I solved it myself evenif not completely,but to some extent.I uninstalled the 2.8 versions of gtk and installed 2.6 versions of them.but now I am not getting any error of "import wx",but instead I get "import wxgui" error and still not able to execute graphical sinks.

---

