---
title: "Error Package citadel-server is not configured yet."
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by NiketGupta on 2011-06-07
I am having the following error. I am a beginner please help me out

hackers@hackers-G31M-ES2L:~$ sudo aptitude upgrade
[sudo] password for hackers: 
The following partially installed packages will be configured:
  citadel-mta citadel-server 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up citadel-server (7.84-3) ...
export: 116: 300: bad variable name
dpkg: error processing citadel-server (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of citadel-mta:
 citadel-mta depends on citadel-server (>= 7.50); however:
  Package citadel-server is not configured yet.
dpkg: error processing citadel-mta (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 citadel-server
 citadel-mta
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up citadel-server (7.84-3) ...
export: 116: 300: bad variable name
dpkg: error processing citadel-server (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of citadel-mta:
 citadel-mta depends on citadel-server (>= 7.50); however:
  Package citadel-server is not configured yet.
dpkg: error processing citadel-mta (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 citadel-server
 citadel-mta
 

Niket

---

