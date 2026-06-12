---
title: "software-center broken and not fixable by a reinstall in 11.04"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by grooverunner on 2011-07-26
Software-center died after installing Picasa on my fresh 11.04 install.

When I run the command in the terminal, this is what I get:

Traceback (most recent call last):
  File "/usr/bin/software-center", line 44, in <module>
    from softwarecenter.utils import ExecutionTime
  File "/usr/share/software-center/softwarecenter/utils.py", line 40, in <module>
    from config import get_config
  File "/usr/share/software-center/softwarecenter/config.py", line 19, in <module>
    import ConfigParser
ImportError: No module named ConfigParser

Additionally, any package I have tried to install in Synaptic (including reinstalling software-center) since the problem cropped up returns this error:

E: /var/cache/apt/archives/python-configglue_0.9pre1-0ubuntu1_all.deb: subprocess new pre-removal script returned error exit status 1
E: /var/cache/apt/archives/software-center_4.0.4_all.deb: subprocess new pre-removal script returned error exit status 1

Is there anything I can do to fix this?
Many thanks
GR.

---

### Post by jerrrys on 2011-07-26
try this:

open a terminal and enter

sudo apt-get clean && sudo apt-get update

then try the software center.  
if this does not work, please post back errors

---

### Post by camilo23 on 2011-09-06
i tried this is the errors it gives me idk what to do it opens up it just doesnt show the actual software is weird


"E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read."
any help?

> **jerrrys said:**
> try this:

open a terminal and enter

sudo apt-get clean && sudo apt-get update

then try the software center.  
if this does not work, please post back errors

---

### Post by raja.genupula on 2011-09-06
```
sudo gedit /etc/apt/sources.list.d/playonlinux.list
```

looking like error in your sources . give us the file data

---

