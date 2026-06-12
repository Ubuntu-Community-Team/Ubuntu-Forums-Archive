---
title: "Ppa with python-software properties in Debian"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by Computergeoffrey on 2011-12-13
I installed python-software-properties to have ubuntu ppa's on debian. I did this: sudo add-apt-repository ppa:marlin-devs/marlin-daily
and i get this:

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 65, in <module>
    if not sp.add_source_from_line(line):
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 630, in add_source_from_line
    (deb_line, file) = expand_ppa_line(line.strip(), self.distro.codename)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 47, in expand_ppa_line
    sourceslistd = apt_pkg.Config.find_dir("Dir::Etc::sourceparts")
AttributeError: 'module' object has no attribute 'Config'

Does someone know how to fix it? Kind regards,
Geoffrey

---

