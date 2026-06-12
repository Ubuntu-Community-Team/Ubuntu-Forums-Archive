---
title: "problems with upgrade"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by restless on 2008-03-04
hey everyone...

this is what pops up after i try to update the system:

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
and this is what i get from the apt.log 

Starting
Starting 2
Investigating kaffeine
Package kaffeine has broken dep on kaffeine-xine
  Considering kaffeine-xine 0 as a solution to kaffeine 1
  Added kaffeine-xine to the remove list
  Fixing kaffeine via remove of kaffeine-xine
Done
Starting
Starting 2
Investigating debootstrap-udeb
Package debootstrap-udeb has broken dep on mounted-partitions
Done
ERROR:root:Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'
Starting
Starting 2
Investigating kaffeine
Package kaffeine has broken dep on kaffeine-xine
  Considering kaffeine-xine 0 as a solution to kaffeine 1
  Added kaffeine-xine to the remove list
  Fixing kaffeine via remove of kaffeine-xine
Done
Starting
Starting 2
Investigating debootstrap-udeb
Package debootstrap-udeb has broken dep on mounted-partitions
Done
ERROR:root:Cache can not be locked (E:Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable), E:Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?)


any idea on how to fix this?
shall i just reinstall kaffeine ?

thank you in advance
Lor

---

### Post by taurus on 2008-03-04
Down down update-manager and others like Add/Remove or synaptic if you have them open.  Then, open a terminal and post the outputs of these two commands.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by restless on 2008-03-04
that easy...
thank you taurus...

i was about to try it before...but thought i might ask for some help..
thanx a lot
Lor

---

### Post by restless on 2008-03-09
hey.,..

the update/upgrade works, but I still have the same problem of a sorf of "unfinished" update that can't complete when i use the normal updating program...
any idea on how i could change the file that stops the update from crashing??

---

### Post by taurus on 2008-03-09
Which app and what is the error message?

---

### Post by restless on 2008-03-11
ok, fixed..

the problem was with some files belonging to kaffeine...
i just uninstalled and reinstalled it...
works fine now..

lor

---

