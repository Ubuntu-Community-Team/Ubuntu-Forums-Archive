---
title: "error while installing reconstructor-engine_3.2.3_all.deb"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by connect2jan on 2011-02-19
janu@janu:~/Downloads$ sudo dpkg -i reconstructor-engine_3.2.3_all.deb
[sudo] password for janu: 
Selecting previously deselected package reconstructor-engine.
(Reading database ... 127917 files and directories currently installed.)
Unpacking reconstructor-engine (from reconstructor-engine_3.2.3_all.deb) ...
dpkg: dependency problems prevent configuration of reconstructor-engine:
 reconstructor-engine depends on kpartx; however:
  Package kpartx is not installed.
 reconstructor-engine depends on mbr; however:
  Package mbr is not installed.
dpkg: error processing reconstructor-engine (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
[B]Processing triggers for python-support ...
[/B]Errors were encountered while processing:
what is that error
can any one provide solution for this

---

### Post by wojox on 2011-02-19
Install the packages it's complaining about.

---

