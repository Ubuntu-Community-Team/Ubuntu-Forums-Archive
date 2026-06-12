---
title: "[SOLVED] Software Sources wont load. Errors in thread."
date: 2008-06-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-06-17
No idea why it suddenly stopped working. But the errors below probably point to an error in the file.

```
 gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
Traceback (most recent call last):
t/__init__.py:18: FutureWarning: apt API not stable yet
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 78, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 516, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.5/site-packages/aptsources/distro.py", line 85, in get_sources
    "Error: could not find a distribution template")
aptsources.distro.NoDistroTemplateException
```

Did the aptitude stuff and got it back but now I cant tick important security updates.

---

