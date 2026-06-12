---
title: "&quot;Screens and Graphics&quot; not working after Gutsy upgrade"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by djerveren on 2007-10-19
After a successful upgrade from Feisty using update-manager, displayconfig-gtk fails to start and produces a python trackback message hinting about XrandR problems:

```
daniel@beast:~ $ sudo /usr/bin/displayconfig-gtk
Traceback (most recent call last):
  File "/usr/bin/displayconfig-gtk", line 75, in <module>
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 190, in __init__
    debug_scan_pci_filename=self.options.pcitable)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 79, in __init__
    self.x_live_info = xf86misc.XF86Server()
  File "/var/lib/python-support/python2.5/xf86misc.py", line 145, in __init__
    self.screens.append(XF86Screen(self.display,i))
  File "/var/lib/python-support/python2.5/xf86misc.py", line 39, in __init__
    self._load()
  File "/var/lib/python-support/python2.5/xf86misc.py", line 43, in _load
    (rc,x,y) = ixf86misc.XRRQueryExtension(self.display)
AttributeError: 'module' object has no attribute 'XRRQueryExtension'
```

Since I'm not very familiar with python, perhaps someone could point me in the right direction to solve this problem.

---

