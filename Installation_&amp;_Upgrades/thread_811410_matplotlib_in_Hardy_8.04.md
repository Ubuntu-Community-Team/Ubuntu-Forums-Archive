---
title: "matplotlib in Hardy 8.04"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by mrouault on 2008-05-29
Hi,

I am struggling with matplotlib installation in hardy 8.04. All ther python packages install well, but after installing matplotlib, I can not list my modules anymore under the help(), nor can I import pylab in python. Any ideas? Here is the message I get when trying to list my modules:

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/site.py", line 342, in __call__
    return pydoc.help(*args, **kwds)
  File "/usr/lib/python2.5/pydoc.py", line 1649, in __call__
    self.interact()
  File "/usr/lib/python2.5/pydoc.py", line 1667, in interact
    self.help(request)
  File "/usr/lib/python2.5/pydoc.py", line 1683, in help
    elif request == 'modules': self.listmodules()
  File "/usr/lib/python2.5/pydoc.py", line 1804, in listmodules
    ModuleScanner().run(callback)
  File "/usr/lib/python2.5/pydoc.py", line 1855, in run
    for importer, modname, ispkg in pkgutil.walk_packages():
  File "/usr/lib/python2.5/pkgutil.py", line 110, in walk_packages
    __import__(name)
  File "/usr/lib/python2.5/site-packages/matplotlib/__init__.py", line 641, in <module>
    rcParams = rc_params()
  File "/usr/lib/python2.5/site-packages/matplotlib/__init__.py", line 564, in rc_params
    fname = matplotlib_fname()
  File "/usr/lib/python2.5/site-packages/matplotlib/__init__.py", line 485, in matplotlib_fname
    oldname = os.path.join( os.getcwd(), '.matplotlibrc')
OSError: [Errno 2] No such file or directory

---

