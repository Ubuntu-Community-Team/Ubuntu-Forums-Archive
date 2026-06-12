---
title: "matplotlib can't be used when I upgrade to feisty"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by wangmm on 2007-02-16
cat /etc/issue
Ubuntu feisty (development branch) \n \l
-----------------------------------------------------------------------
when I used the matplotlib by:
$ ipython --pylab

Error report as fellow:
-----------------------------------------------------------------------
The import of the numpy version of the _transforms module,
_ns_transforms, failed.  This is is either because numpy was
unavailable when matplotlib was compiled, because a dependency of
_ns_transforms could not be satisfied, or because the build flag for
this module was turned off in setup.py.  If it appears that
_ns_transforms was not built, make sure you have a working copy of
numpy and then re-install matplotlib. Otherwise, the following
traceback gives more details:

Traceback (most recent call last):
  File "/usr/bin/ipython", line 27, in <module>
    IPython.Shell.start().mainloop()
  File "/usr/lib/python2.5/site-packages/IPython/Shell.py", line 1034, in start
    return shell(user_ns = user_ns)
  File "/usr/lib/python2.5/site-packages/IPython/Shell.py", line 945, in __init__
    shell_class=MatplotlibMTShell)
  File "/usr/lib/python2.5/site-packages/IPython/Shell.py", line 622, in __init__
    on_kill=[mainquit])
  File "/usr/lib/python2.5/site-packages/IPython/ipmaker.py", line 90, in make_IPython
    embedded=embedded,**kw)
  File "/usr/lib/python2.5/site-packages/IPython/Shell.py", line 506, in __init__
    user_ns,b2 = self._matplotlib_config(name,user_ns)
  File "/usr/lib/python2.5/site-packages/IPython/Shell.py", line 397, in _matplotlib_config
    from matplotlib import backends
  File "/usr/lib/python2.5/site-packages/matplotlib/backends/__init__.py", line 55, in <module>
    new_figure_manager, draw_if_interactive, show = pylab_setup()
  File "/usr/lib/python2.5/site-packages/matplotlib/backends/__init__.py", line 23, in pylab_setup
    globals(),locals(),[backend_name])
  File "/usr/lib/python2.5/site-packages/matplotlib/backends/backend_gtk.py", line 19, in <module>
    from matplotlib.backend_bases import RendererBase, GraphicsContextBase, \
  File "/usr/lib/python2.5/site-packages/matplotlib/backend_bases.py", line 13, in <module>
    from patches import Rectangle
  File "/usr/lib/python2.5/site-packages/matplotlib/patches.py", line 6, in <module>
    from artist import Artist, setp
  File "/usr/lib/python2.5/site-packages/matplotlib/artist.py", line 4, in <module>
    from transforms import identity_transform
  File "/usr/lib/python2.5/site-packages/matplotlib/transforms.py", line 223, in <module>
    from _transforms import Value, Point, Interval, Bbox, Affine
  File "/usr/lib/python2.5/site-packages/matplotlib/_transforms.py", line 17, in <module>
    from matplotlib._ns_transforms import *
[COLOR="Red"]ImportError: No module named _ns_transforms[/COLOR]

---

### Post by wangmm on 2007-02-16
OK.
Version informtion as fellow:
---------------------------------------------------------------------

dpkg -l python-matplotlib python-numpy
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  [COLOR="Red"]python-matplot 0.87.7-0.1[/COLOR]     python based plotting system in a style simi
ii  [COLOR="Red"]python-numpy   1.0.1-1[/COLOR]        Numerical Python adds a fast array facility

---

### Post by Robsteranium on 2008-07-01
Above helped me too.  Still stuck tho...

Using Febrl-0.4.02 (from sourceforge):
```
python guiFebrl.py 
Febrl directory: ~~~/febrl-0.4.02
WARNING:root:Cannot import Numeric and PyML modules

```

Any ideas?

```
dpkg -l python-matplotlib python-numpy
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  python-matplot 0.91.2-0ubuntu Python based plotting system in a style simi
ii  python-numpy   1:1.0.4-6ubunt Numerical Python adds a fast array facility 

```

---

