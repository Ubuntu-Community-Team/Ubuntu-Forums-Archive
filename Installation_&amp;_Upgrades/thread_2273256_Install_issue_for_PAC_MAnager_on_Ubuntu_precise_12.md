---
title: "Install issue for PAC MAnager on Ubuntu precise 12.04"
date: 2015-04-11
forum: Installation &amp; Upgrades
---

### Post by edwin22 on 2015-04-11
Hi Guys,

I've been fighting with this error during the installation of Pac Manager for some time and cannot seem to get it fixed:

$ sudo apt-get install pac
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 pac : Depends: libgnome2-vte-perl but it is not going to be installed
       Depends: libgtk2-appindicator-perl but it is not installable
E: Unable to correct problems, you have held broken packages.

Im going in circles...

All help is welcome!

---

### Post by edwin22 on 2015-04-12
Solved it myself after trial and error.
Good old RTFM

---

