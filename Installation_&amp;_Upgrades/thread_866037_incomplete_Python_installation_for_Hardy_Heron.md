---
title: "incomplete Python installation for Hardy Heron?"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by danzinho on 2008-07-21
Dear all

I've just put 8.04 on a new Dell box and almost everything works beautifully.  However, I'm trying to install something with scons and meeting a python problem

I get

$ scons rosetta++ mode=release
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/scons", line 39, in <module>
    import os
ImportError: No module named os

I get the impression that this should be there by default.  Should it?  How to get it?

My /var/lib/python-support/python2.5/ directory just has these .py files

Thanks in advance for your help

dbus_bindings.py
displayconfigabstraction.py
displayconfig-hwprobe.py
displayconfig-restore.py
drivedetect.py
drv_libxml2.py
execwithcapture.py
GnuPGInterface.py
infimport.py
libxml2.py
MicroHAL.py
pygtk.py
ScanPCI.py
wineread.py
winewrite.py
xf86misc.py
xorgconfig.py

---

### Post by danzinho on 2008-07-21
I just realised that os.py IS present, but in a different place /usr/lib/python2.5

If I do 

export PYTHON_HOME=/usr/lib/python2.5

I can now import os into Python started on the command line.  However, this doesn't seem to help, even when put in .bashrc,  with the scons script which starts 

#! /usr/bin/env python

How can I tell the scons script where PYTHON_HOME is?

Thanks

---

### Post by danzinho on 2008-07-21
Sorry, I was mistaken.  Importing only works in the /usr/lib/python2.5 directory.  Setting PYTHON_HOME *doesn't help*

---

