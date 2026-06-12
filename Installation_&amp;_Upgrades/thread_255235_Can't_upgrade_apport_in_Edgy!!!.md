---
title: "Can't upgrade apport in Edgy!!!"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by tvlad on 2006-09-11
Recently i upgraded to the latest debs in the Edgy Eft repository.

The problem i have is that i can't upgrade or remove apport, it always give me the same error message. i tried apt-get -f remove/install, dpkg --configure -a , and still nothing.

root@darkstar:/var/cache/apt/archives/partial# apt-get install apport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apport
1 upgraded, 0 newly installed, 0 to remove and 59 not upgraded.
Need to get 0B/18.6kB of archives.
After unpacking 24.6kB of additional disk space will be used.
Selecting previously deselected package apport.
(Reading database ... 121723 files and directories currently installed.)
Preparing to replace apport 0.18 (using .../archives/apport_0.20_all.deb) ...
 * Stopping automatic crash report generation: apport                           invoke-rc.d: initscript apport, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
 * Stopping automatic crash report generation: apport                           invoke-rc.d: initscript apport, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/apport_0.20_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_0.20_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


root@darkstar:/var/cache/apt/archives/partial# apt-get -f remove apport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  apport
0 upgraded, 0 newly installed, 1 to remove and 59 not upgraded.
Need to get 0B of archives.
After unpacking 131kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 121722 files and directories currently installed.)
Removing apport ...
 * Stopping automatic crash report generation: apport                           invoke-rc.d: initscript apport, action "stop" failed.
dpkg: error processing apport (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 apport
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by tvlad on 2006-09-12
Up!

---

### Post by abeowitz on 2006-09-30
as root, delete /var/lib/dpkg/info/apport.prerm

This seemed to work for me...

---

