---
title: "[SOLVED] Software Sources Manager won't start"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by jdackle on 2008-11-27
Hi,

The Software Sources Manager application will not start, either called from the menu, from synaptic or from the command-line.

Synaptic and Update-Manager work correctly.

apt-get works too and *apt-get update* will indeed update any changes made to /etc/apt/sources.list

When run from the command-line:
```
$ gksu /usr/bin/software-properties-gtk
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet  warnings.warn("apt API not stable yet", FutureWarning)
```

Sometimes, a longer message is given:
```
$ gksu /usr/bin/software-properties-gtkTraceback (most recent call last):
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


I have no clue whether it is related or not but this problem started after I tinkered with dpkg -i --force-depends ('cause of openoffice.org3 and 2.4...)

Can someone tell me whether I've actually messed up something (and possibly how to fix it) or shall I just file a bug-report (there may already be one, haven't checked)?


[COLOR="Red"]EDIT: Running 8.04.1 Hardy Heron.
WAIT! Just typed (to double-check it wasn't just 8.04 or something) and got this on the terminal:```
$ sudo lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid
``` :confused:

I'd tried to install Intrepid but it was unusable. So I reinstalled Hardy from the Live CD. As the installer said all system folders (/boot, /etc, /usr, ...) would be deleted, I didn't bother to actually reformat the partition...

Now I have to reinstall and reconfigure everything again?](*,)[/COLOR]

---

