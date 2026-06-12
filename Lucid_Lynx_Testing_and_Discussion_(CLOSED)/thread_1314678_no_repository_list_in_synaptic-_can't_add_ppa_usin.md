---
title: "no repository list in synaptic- can't add ppa using add-repository-ppa"
date: 2009-11-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lonniehenry on 2009-11-04
I installed new partition and a new install of karmic, changed karmic to lucid in sources, and did the updates.  Work fine with no problems.  After a couple of day I went to add a PPA to the sources in synaptic.  When I open repositories, it doesn't open.  I tried from the menu to open software sources and it doesn't open.  I tried to add the ppa using add-repository-ppa in terminal and it fails.  I opened synaptic using terminal and get the following:
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 110, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 87, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 536, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
 
Is this caused by not having the toolchain loaded?  I am able to use synaptic to do the updates that appear.  I just can't add PPAs

---

### Post by LKjell on 2009-11-04
Hi,

[http://ubuntuforums.org/showthread.php?t=1308574](http://ubuntuforums.org/showthread.php?t=1308574)

---

### Post by lonniehenry on 2009-11-04
LKjell,  thanks.  that sorted out the problem.  I have jumped in on the new repos before but not usually this early.  I appreciate the quick response.
L>

---

