---
title: "Repository error messages when upgrading to Firefox 4"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by Mattheu on 2011-05-30
I'm running Joli OS 1.2 and have just tried to upgrade Firefox from 3.6 to 4.  The first of the three commands I was trying to use threw up the errors shown below (not sure if these are connected to me using Python a few days ago, as shown in LXF magazine): 

```
matthew@matthew-jolicloud:~$ sudo add-apt-repository ppa:mozillateam/firefox-stable
[sudo] password for matthew: 
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 40, in <module>
    sp = SoftwareProperties(options)    
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 538, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
matthew@matthew-jolicloud:~$ 
```I have no idea what to do next.

---

