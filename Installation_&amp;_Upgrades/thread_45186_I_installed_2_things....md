---
title: "I installed 2 things..."
date: 2005-06-29
forum: Installation &amp; Upgrades
---

### Post by kona0197 on 2005-06-29
And they are NOT showing up anywhere - but according to apt-get and synaptic they were installed. 

The 2 programs were hotway and gotmail. I even rebooted and no success. 

Ideas?

(And please some tell me how to run apps in root!)

---

### Post by djg on 2005-06-29
[QUOTE=kona0197]And they are NOT showing up anywhere - but according to apt-get and synaptic they were installed. 

The 2 programs were hotway and gotmail. I even rebooted and no success. 

Ideas?

(And please some tell me how to run apps in root!)[/QUOTE]
 The hotway package should installs "hotwayd" into /usr/bin, and gotmail should install "gotmail" into the same directory.  Try running ls -l /usr/bin/hotwayd to ensure they're not there first.

Regarding the root issue, Ubuntu doesn't use a root account per se, but you can run an application with root privileges using the "sudo" command.  When prompted for a password, enter your own password.

---

