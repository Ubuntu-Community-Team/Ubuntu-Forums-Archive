---
title: "Error while updateing"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by genseek on 2008-08-14
Dear all,

I am new to Linux and Ubuntu. Usually if I get a problem I google a solution, but this time it did not work. 

While updating the system I get the following error:

> Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up initramfs-tools (0.85eubuntu39.2) ...
: not foundmfs-tools/conf.d/resume: 2: q
dpkg: error processing initramfs-tools (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)


If I try 
> sudo apt-get if install
I get the same. 

While 
> sudo dpkg --configure -a
gives
> Setting up initramfs-tools (0.85eubuntu39.2) ...
: not foundmfs-tools/conf.d/resume: 2: q
dpkg: error processing initramfs-tools (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of cdemu-daemon:
 cdemu-daemon depends on libmirage; however:
  Package libmirage is not installed.
 cdemu-daemon depends on vhba-module; however:
  Package vhba-module is not installed.
dpkg: error processing cdemu-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcdemu:
 gcdemu depends on cdemu-daemon; however:
  Package cdemu-daemon is not configured yet.
dpkg: error processing gcdemu (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 initramfs-tools
 cdemu-daemon
 gcdemu


I could not fine any of the packages quoted in last quote...

Thank you all for suggestions.

---

### Post by genseek on 2008-08-15
I still hope for an answer:(

---

