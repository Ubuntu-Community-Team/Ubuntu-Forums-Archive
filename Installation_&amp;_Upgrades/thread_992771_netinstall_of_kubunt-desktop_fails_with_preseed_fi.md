---
title: "netinstall of kubunt-desktop fails with preseed file"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by hlynur on 2008-11-25
I'm setting up a local mirror and installation server of ubuntu 8.04. I have a fai installation server of ubuntu 6.06 but im getting lazy to upgrade that one and decided to have a look at net install with preceed files etc..

anyway:

installing ubuntu-desktop goes fine e.g. in the preseed file:

tasksel tasksel/first multiselect standard, ubuntu-desktop

but if choosing kubuntu the install halts with a k3b dependency problem.

tasksel tasksel/first multiselect standard, kubuntu-desktop

from syslog:

Nov 25 11:15:01 in-target: The following packages have unmet dependencies:
Nov 25 11:15:01 in-target:   k3b: Depends: libk3b3 but it is not going to be installed
Nov 25 11:15:01 in-target: E: Broken packages
Nov 25 11:15:01 in-target: tasksel: aptitude failed (100)
Nov 25 11:15:01 main-menu[3381]: WARNING **: Configuring 'pkgsel' failed with error code 1 
Nov 25 11:15:01 main-menu[3381]: WARNING **: Menu item 'pkgsel' failed


now I have verified the libk3b3 and k3b packages are on my mirror and they are intact. 


Furthermore choosing ubuntu and then later in the installation process include kubuntu-desktop yields no problems. 

tasksel tasksel/first multiselect standard, ubuntu-desktop
d-i pkgsel/include string kubuntu-desktop

anybody been messing with this ?

Cheers / Thor

---

### Post by hlynur on 2008-11-25
ok found a quick workaround: 

tasksel tasksel/first multiselect standard, ubuntu-minimal
d-i pkgsel/include string kubuntu-desktop

but still don't get why 

tasksel tasksel/first multiselect standard, kubuntu-desktop
doesn't work !

---

