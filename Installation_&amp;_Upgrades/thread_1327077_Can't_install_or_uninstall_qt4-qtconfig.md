---
title: "Can't install or uninstall qt4-qtconfig"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by alamuru420123 on 2009-11-15
I've been trying to setup kdevelop on my system and was in the process of installing the qt4 designer along with the docs and anything else that looked necessary to me.

However, while installing qt4-qtconfig, kde got stuck and even the mouse froze. I could only do a hard reboot. Now I'm unable to do anything with it. I keep getting the following error with synaptic if I try to uninstall or reinstall it:

```
(Reading database ... 212306 files and directories currently installed.)
Removing qt4-qtconfig ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing qt4-qtconfig (--purge):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 qt4-qtconfig
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


```

Any help will be highly appreciated!

Thanks!

---

### Post by alamuru420123 on 2009-11-15
Fixed it using this post here:

[http://www.linuxquestions.org/questions/showthread.php?p=3040967#post3040967](http://www.linuxquestions.org/questions/showthread.php?p=3040967#post3040967)

In short deleted all the files in /var/lib/dpkg/info with the name qt4-qtconfig*

Then installed it again using sudo apt-get install qt4-qtconfig and it went through fine.

---

