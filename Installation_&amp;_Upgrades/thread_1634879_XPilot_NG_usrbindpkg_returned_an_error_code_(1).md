---
title: "XPilot NG /usr/bin/dpkg returned an error code (1)"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by kakila on 2010-12-01
Hi all,
Upgrading to 10.10 I got this error

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libboost-all-dev libboost-date-time-dev libboost-dev libboost-doc
  libboost-filesystem-dev libboost-graph-dev libboost-program-options-dev
  libboost-python-dev libboost-regex-dev libboost-serialization-dev
  libboost-signals-dev libboost-test-dev libboost-thread-dev libboost-wave-dev
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up xpilot-ng-server (1:4.7.3-1.2) ...
chmod: cannot access `/var/run/xpilot-ng-server': No such file or directory
dpkg: error processing xpilot-ng-server (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of xpilot-ng:
 xpilot-ng depends on xpilot-ng-server (>= 1:4.7.3-1.2); however:
  Package xpilot-ng-server is not configured yet.
dpkg: error processing xpilot-ng (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 xpilot-ng-server
 xpilot-ng
E: Sub-process /usr/bin/dpkg returned an error code (1)

The outomatic updated did not reboot automatically. What shall I do? It is safe to reboot my computer?

---

### Post by kakila on 2010-12-01
Ok,
I removed those packages and rebooted, cause some programs where not working.

It looks like I am in the new distro, how can I check everything is Ok?
Is anyway to detect if the distro is half-installe dor something like that?


There are things, like the fonts of the desktop, that make me suspicious...

If now I run
 sudo apt-get dist-upgrade
I get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libboost-all-dev libboost-date-time-dev libboost-dev libboost-doc
  libboost-filesystem-dev libboost-graph-dev libboost-program-options-dev
  libboost-python-dev libboost-regex-dev libboost-serialization-dev
  libboost-signals-dev libboost-test-dev libboost-thread-dev libboost-wave-dev
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.

What is the meaning of that?

Thanks

---

