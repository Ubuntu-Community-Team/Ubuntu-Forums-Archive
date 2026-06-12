---
title: "discrepancy in calculated packages needed to install"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by scottstensland on 2011-08-27
I want to compile from source pygame : package (python-pygame),
strangely, to identify prerequisite packages I am seeing different sets of necessary packages 
across different commands.  

Shouldn't these two command show the same list of needed packages ?
This command :

apt-get build-dep -s python-pygame

lists :

The following NEW packages will be installed:
  libmikmod2 libmikmod2-dev libportmidi-dev libportmidi0 libpython2.6 libsdl-mixer1.2 libsdl-mixer1.2-dev libsmpeg-dev  libsmpeg0 python-all python-all-dev python2.6 python2.6-dev python2.6-minimal sharutils

yet using Update Manager GUI, it lists these packages as "additional required changes" :

libmikmod2
libportmidi0
 libsdl-mixer1.2
libsmpeg0

which matches the same set of needed packages as listed using :

sudo apt-get install python-pygame

Why is build-dep seemingly misleading ?
here is my

python --version
Python 2.7.2+

I seriously doubt the build-dep output should mention python2.6 

Somewhat of a rhetorical question as I usually compile first/ask questions later
but in the interest of possibly fixing build-dep  ...

---

