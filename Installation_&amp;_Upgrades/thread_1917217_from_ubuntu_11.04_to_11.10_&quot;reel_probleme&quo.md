---
title: "from ubuntu 11.04 to 11.10 &quot;reel probleme&quot; is it a bug ?"
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by redsprite on 2012-01-29
[SIZE=2]**root@bt:~# sudo dpkg --configure -a**[/SIZE]
Setting up ruby1.9.1 (1.9.2.290-2) ...
update-alternatives: error: alternative gem can't be master: it is a slave of ruby
dpkg: error processing ruby1.9.1 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up ruby1.8 (1.8.7.352-2) ...
update-alternatives: error: alternative rdoc can't be slave of ruby: it is a master alternative.
dpkg: error processing ruby1.8 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ruby:
 ruby depends on ruby1.8 (>> 1.8.7.334-1); however:
  Package ruby1.8 is not configured yet.
dpkg: error processing ruby (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ruby1.8-full:
 ruby1.8-full depends on ruby1.8; however:
  Package ruby1.8 is not configured yet.
dpkg: error processing ruby1.8-full (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ruby1.9.1-full:
 ruby1.9.1-full depends on ruby1.9.1 (>= 1.9.2.290-2); however:
  Package ruby1.9.1 is not configured yet.
dpkg: error processing ruby1.9.1-full (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ri1.8:
 ri1.8 depends on ruby1.8 (>= 1.8.7.352-2); however:
  Package ruby1.8 is not configured yet.
dpkg: error processing ri1.8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ri1.9.1:
 ri1.9.1 depends on ruby1.9.1 (>= 1.9.2.290-2); however:
  Package ruby1.9.1 is not configured yet.
dpkg: error processing ri1.9.1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ruby-full:
 ruby-full depends on ruby1.8-full (>> 1.8.7.334-1); however:
  Package ruby1.8-full is not configured yet.
dpkg: error processing ruby-full (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ruby1.9.1
 ruby1.8
 ruby
 ruby1.8-full
 ruby1.9.1-full
 ri1.8
 ri1.9.1
 ruby-full
 ------------------------------------------
**[SIZE=2]root@bt:~# sudo apt-get upgrade[/SIZE]**

so whene traying to upgrade to ubuntu11.10 i have that :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libpurple0 nfs-common
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
8 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ruby1.8 (1.8.7.352-2) ...
update-alternatives: error: alternative rdoc can't be slave of ruby: it is a master alternative.
dpkg: error processing ruby1.8 (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ri1.8:
 ri1.8 depends on ruby1.8 (>= 1.8.7.352-2); however:
  Package ruby1.8 is not configured yet.
dpkg: error processing ri1.8 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up ruby1.9.1 (1.9.2.290-2) ...
update-alternatives: error: alternative gem can't be master: it is a slave of ruby
dpkg: error processing ruby1.9.1 (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ri1.9.1:
 ri1.9.1 depends on ruby1.9.1 (>= 1.9.2.290-2); however:
  Package ruby1.9.1 is not configured yet.
dpkg: error processing ri1.9.1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ruby:
 ruby depends on ruby1.8 (>> 1.8.7.334-1); however:
  Package ruby1.8 is not configured yet.
dpkg: error processing ruby (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ruby1.8-full:
 ruby1.8-full depends on ruby1.8; however:
  Package ruby1.8 is not configured yet.
 ruby1.8-full depends on ri1.8; however:
  Package ri1.8 is not configured yet.
dpkg: error processing ruby1.8-full (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ruby-full:
 ruby-full depends on ruby1.8-full (>> 1.8.7.334-1); however:
  Package ruby1.8-full is not configured yet.
dpkg: error processing ruby-full (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ruby1.9.1-full:
 ruby1.9.1-full depends on ruby1.9.1 (>= 1.9.2.290-2); however:
  Package ruby1.9.1 is not configured yet.
 ruby1.9.1-full depends on ri1.9.1 (>= 1.9.2.290-2); however:
  Package ri1.9.1 is not configured yet.
dpkg: error processing ruby1.9.1-full (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 ruby1.8
 ri1.8
 ruby1.9.1
 ri1.9.1
 ruby
 ruby1.8-full
 ruby-full
 ruby1.9.1-full
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

