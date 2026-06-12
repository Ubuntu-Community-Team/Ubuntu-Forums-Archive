---
title: "use some packages from breezy but not wholly upgrade to"
date: 2005-12-02
forum: Installation &amp; Upgrades
---

### Post by tolgas on 2005-12-02
hi,

Currently i use 5.04 and want to use some specific packages, say it, libwxgtk2.6-0 (which only appears to be in breezy, not in hoary), but i do not want to wholly upgrade to breezy right now.

When i try to install the package from my local repository, synaptic tells me that she is going to remove my basic essential hoary packages g++, gcc, ubuntu-base, etc ! When i try from a terminal by apt-get, it does not let me either, says 'broken packages'

i also have some other packages that need breezy versions of some packages as dependencies, and though i add them to my local repository, synaptic prefers the hoary ones, and refuses to upgrade them....:( 

is there any way around this? :confused: 

dark

---

### Post by Xian on 2005-12-02
[QUOTE=tolgas]
When i try to install the package from my local repository, synaptic tells me that she is going to remove my basic essential hoary packages g++, gcc, ubuntu-base, etc ! When i try from a terminal by apt-get, it does not let me either, says 'broken packages'[/QUOTE]
Apparently the packages you are wanting to install depend upon other system files that would also need to be upgraded. In short, they will not work unless this occurs.

---

