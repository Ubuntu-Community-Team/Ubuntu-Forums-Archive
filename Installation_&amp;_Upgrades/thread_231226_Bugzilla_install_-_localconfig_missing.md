---
title: "Bugzilla install - localconfig missing"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by Jorre on 2006-08-07
Hi, 

I'm trying to install Bugzilla on my Ubuntu server (Linux Hagar 2.6.12-9-386 #1 Mon Oct 10 2005 i686 GNU/Linux).

I'm executing the apt-get command: apt-get install bugzilla 
and get the following output:

Reading package lists... Done
Building dependency tree... Done
bugzilla is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up bugzilla (2.18.4-1) ...
Database bugzilla already exists, skipping database creation.
Can't rename /etc/bugzilla/localconfig : No such file or directory
dpkg: error processing bugzilla (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 bugzilla
E: Sub-process /usr/bin/dpkg returned an error code (1)

When looking in /etc/bugzilla I only see the params file and the sites directory which is empty...

I can see the localconfig file is missing, so is there a way to retrieve that somewhere?

Thanks,
Jorre.

---

