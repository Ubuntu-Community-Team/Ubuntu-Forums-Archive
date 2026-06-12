---
title: "unable to install packages"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by malakar.subhendu on 2012-05-04
whenever i'm trying to install a software from the terminal it shows:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 g++-4.6 : Depends: gcc-4.6-base (= 4.6.3-1ubuntu4) but 4.6.3-1ubuntu5 is to be installed
           Depends: gcc-4.6 (= 4.6.3-1ubuntu4) but 4.6.3-1ubuntu5 is to be installed
           Depends: libstdc++6-4.6-dev (= 4.6.3-1ubuntu4) but 4.6.3-1ubuntu5 is to be installed
 libstdc++6-4.6-dev : Depends: g++-4.6 (= 4.6.3-1ubuntu5) but 4.6.3-1ubuntu4 is to be installed
 synaptic : Depends: libept1.4.12 but it is not going to be installed
            Depends: libvte9 (>= 1:0.24.0) but it is not going to be installed
            Recommends: rarian-compat but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

when doing 'apt-get -f install' it shows:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  g++-4.6
Suggested packages:
  g++-4.6-multilib gcc-4.6-doc libstdc++6-4.6-dbg
The following packages will be upgraded:
  g++-4.6
1 upgraded, 0 newly installed, 0 to remove and 68 not upgraded.
3 not fully installed or removed.
Need to get 0 B/6,954 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of g++-4.6:
 g++-4.6 depends on gcc-4.6-base (= 4.6.3-1ubuntu4); however:
  Version of gcc-4.6-base on system is 4.6.3-1ubuntu5.
 g++-4.6 depends on gcc-4.6 (= 4.6.3-1ubuntu4); however:
  Version of gcc-4.6 on system is 4.6.3-1ubuntu5.
 g++-4.6 depends on libstdc++6-4.6-dev (= 4.6.3-1ubuntu4); however:
  Version of libstdc++6-4.6-dev on system is 4.6.3-1ubuntu5.
dpkg: error processing g++-4.6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libstdc++6-4.6-dev:
 libstdc++6-4.6-dev depends on g++-4.6 (= 4.6.3-1ubuntu5); however:
  Version of g++-4.6 on system is 4.6.3-1ubuntu4.
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    dpkg: error processing libstdc++6-4.6-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g++:
 g++ depends on g++-4.6 (>= 4.6.3-1~); however:
  Package g++-4.6 is not configured yet.
dpkg: error processing g++ (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 g++-4.6
 libstdc++6-4.6-dev
 g++
E: Sub-process /usr/bin/dpkg returned an error code (1)


what to do for this.

when trying to install from ubuntu software center, it shows package catalog is broken. repair needed. an when trying to repair it fails.

---

### Post by malakar.subhendu on 2012-05-04
please help me. 
unable to install java,etc. needed for my studies.

---

