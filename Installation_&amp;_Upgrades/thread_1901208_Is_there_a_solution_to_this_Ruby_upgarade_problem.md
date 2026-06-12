---
title: "Is there a solution to this Ruby upgarade problem ?"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2011-12-28
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
11 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up ruby1.8 (1.8.7.352-2) ...
update-alternatives: error: alternative irb can't be slave of ruby: it is a master alternative.
dpkg: error processing ruby1.8 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ruby:
 ruby depends on ruby1.8 (>> 1.8.7.334-1); however:
  Package ruby1.8 is not configured yet.
dpkg: error processing ruby (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rake:
 rake depends on ruby; however:
  Package ruby is not configured yet.
  Package ruby1.8 which provides ruby is not configured yet.
dpkg: error processing rake (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ri1.8:
 ri1.8 depends on ruby1.8 (>= 1.8.7.352-2); however:
  Package ruby1.8 is not configured yet.
dpkg: error processing ri1.8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ri:
 ri depends on ri1.8 (>> 1.8.7.334-1); however:
  Package ri1.8 is not confNo apport report written because the error message indicates its a followup error from a previous failure.
               No apport report written because the error message indicates its a followup error from a previous failure.
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
         igured yet.
dpkg: error processing ri (--configure):
 dependency problems - leaving unconfigured
Setting up ruby1.9.1 (1.9.2.290-2) ...
update-alternatives: error: alternative irb can't be slave of ruby: it is a master alternative.
dpkg: error processing ruby1.9.1 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ri1.9.1:
 ri1.9.1 depends on ruby1.9.1 (>= 1.9.2.290-2); however:
  Package ruby1.9.1 is not configured yet.
dpkg: error processing ri1.9.1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ruby1.8-full:
 ruby1.8-full depends on ruby1.8; however:
  Package ruby1.8 is not configured yet.
 ruby1.8-full depends on ri1.8; however:
  Package ri1.8 is not configured yet.
dpkg: error processing ruby1.8-full (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ruby-full:
 ruby-full depends on ruby1.8-full (>> 1.8.7.334-1); however:
  Package ruby1.8-full is not configured yet.
dpkg: error processing ruby-full (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuratiNo apport report written because MaxReports is reached already
                                                                                                           No apport report written because MaxReports is reached already
                                                   No apport report written because MaxReports is reached already
                                                                                                                 No apport report written because MaxReports is reached already
                                                         No apport report written because MaxReports is reached already
 No apport report written because MaxReports is reached already
                                                               on of ruby1.9.1-full:
 ruby1.9.1-full depends on ruby1.9.1 (>= 1.9.2.290-2); however:
  Package ruby1.9.1 is not configured yet.
 ruby1.9.1-full depends on ri1.9.1 (>= 1.9.2.290-2); however:
  Package ri1.9.1 is not configured yet.
dpkg: error processing ruby1.9.1-full (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rubygems:
 rubygems depends on ruby1.8; however:
  Package ruby1.8 is not configured yet.
dpkg: error processing rubygems (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ruby1.8
 ruby
 rake
 ri1.8
 ri
 ruby1.9.1
 ri1.9.1
 ruby1.8-full
 ruby-full
 ruby1.9.1-full
 rubygems
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

