---
title: "install OpenAl howto?"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by attilio on 2005-11-13
hi 
im getting openal errors when compiling from source, trying to find out howto install openal, anyone know? 

heres the error: 
checking for OpenGL support... yes
checking for OpenAL... checking for openal-config... no
*** The openal-config script installed by OpenAL could not be found
*** Make sure openal-config is in your path, or set the OPENAL_CONFIG
*** environment variable to the full path to openal-config.
checking for OpenAL compilation... no
configure: error: *** Can't find the openal library. Try: [http://www.openal.org/](http://www.openal.org/)

---

### Post by Death4Hire on 2006-10-03
Yes, I also need to know how to install OpenAl. There's no openal in the Synaptic tool!

---

### Post by cborga1985 on 2006-11-04
**OpenAL**
```
sudo apt-get install libopenal0a libopenal-dev
```

**Alut**
```
sudo apt-get install libalut0 libalut-dev
```

Not trying to get my count up. Just thought I would put this up for anybody having trouble with this since you need it to compile VDrift.

---

### Post by sinaen on 2007-08-10
i cannot install libalut0 it's broken maybe i have the wrong repositories. i run feisty i get this error message when i try to install libalut0

yoshi@idissla:/etc/default$ sudo aptitude install libalut0
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for libalut0

sudo aptitude install vdrift
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  vdrift
Need to get 0B of archives. After unpacking 1397kB will be used.
The following packages have unmet dependencies:
  vdrift: Depends: libalut0 which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

---

