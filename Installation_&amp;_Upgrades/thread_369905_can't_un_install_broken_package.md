---
title: "can't un install broken package"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by rovernaut on 2007-02-25
I'm Trying to remove a broken package 'linux-igd'
It keeps appearing in synaptic as an error everytime I upgrade anything.
I can't uninstall it within synaptic.
I am still learning on linux ( newbie)
I tried removing it  in terminal with  aptitude and get this.


'Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
  linux-igd{p}
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 201kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 166226 files and directories currently installed.)
Removing linux-igd ...
External interface not specified in /etc/default/upnpd
invoke-rc.d: initscript upnpd, action "stop" failed.
dpkg: error processing linux-igd (--purge):
 subprocess pre-removal script returned error exit status 1
External interface not specified in /etc/default/upnpd
invoke-rc.d: initscript upnpd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-igd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

Any Ideas?
'

---

### Post by r4ik on 2007-02-25
In synaptic edit - fix broken packages

---

### Post by rovernaut on 2007-02-26
thanks, but it didn't work. ;-(

---

