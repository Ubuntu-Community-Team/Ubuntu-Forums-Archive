---
title: "Messed up 12.04 trying new desktops (gnome3)"
date: 2012-11-10
forum: Installation &amp; Upgrades
---

### Post by johnknott on 2012-11-10
Recovered some sanity after  removing gnome 3 and etc/apt/sources.list.d/  content


Try to install gnome shell get

ubuntu@unassigned-hostname:~$ sudo apt-get install gnome-shell
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 gnome-shell : Depends: gir1.2-gjsdbus-1.0 but it is not going to be installed
               Recommends: gnome-session-fallback but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ubuntu@unassigned-hostname:~$ 


Tried to install Cinnamon installs but wont run from Logon choser!

Help appreciated

---

### Post by ibjsb4 on 2012-11-10
Something is a little screwy here.  Gnome3 cannot be removed, ubuntu 12o4 and unity depend on it.  If you did truly remove gnome, ubuntu should not even boot.

---

