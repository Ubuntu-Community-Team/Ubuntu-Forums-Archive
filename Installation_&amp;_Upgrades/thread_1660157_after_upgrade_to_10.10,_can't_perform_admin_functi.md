---
title: "after upgrade to 10.10, can't perform admin functions"
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by spongebob331 on 2011-01-05
After a fresh install to 10.10 (though I did preserve my /home partition), I'm unable to add restricted drivers, install updates via update manager, or install software from the software center.  When trying to add an nvidia driver, it says "You are not authorized to perform this action".  With update manager or the software center, the window just flickers and there is no error and nothing happens.  My guess is somehow I'm not setup as an administrator, but the passwd, group, and sudoers files look identical to my 10.04 installation.

Any ideas?

---

### Post by dino99 on 2011-01-05
reboot, then either:

open a terminal:
sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a
( could be long, dont stop it before it ending)

open synaptic (system admin synaptic):
update and make packages maintenace from there

---

