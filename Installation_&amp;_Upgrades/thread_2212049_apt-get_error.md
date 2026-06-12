---
title: "apt-get error"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by isac630728 on 2014-03-19
Please help



```
root@server001:/etc/init# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 mysql-server-5.5 : Breaks: mysql-server (< 5.5.35-0ubuntu0.12.04.2) but 5.5.35-0ubuntu0.12.04.1 is installed
 python2.7 : Depends: python2.7-minimal (= 2.7.3-0ubuntu3.4) but 2.7.3-0ubuntu3.5 is installed
E: Unmet dependencies. Try using -f.






root@server001:/etc/init# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libpython2.7 mysql-server python2.7
Suggested packages:
  python2.7-doc
The following packages will be upgraded:
  libpython2.7 mysql-server python2.7
3 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
18 not fully installed or removed.
Need to get 0 B/3,874 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of python2.7:
 python2.7 depends on python2.7-minimal (= 2.7.3-0ubuntu3.4); however:
  Version of python2.7-minimal on system is 2.7.3-0ubuntu3.5.
dpkg: error processing python2.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpython2.7:
 libpython2.7 depends on python2.7 (= 2.7.3-0ubuntu3.4); however:
  Package python2.7 is not configured yet.
dpkg: error processing libpython2.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python:
 python depends on python2.7 (>= 2.7.3); however:
  Package python2.7 is not configured yet.
dpkg: error processing python (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on python; however:
  Package python is not configured yet.
dpkg: error processing apparmor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent conf
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Configuration of python-apt-common:
 python-apt-common depends on python | python3; however:
  Package python is not configured yet.
  Package python3 is not installed.
dpkg: error processing python-apt-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apt:
 python-apt depends on python2.7; however:
  Package python2.7 is not configured yet.
 python-apt depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-apt depends on python (<< 2.8); however:
  Package python is not configured yet.
 python-apt depends on python-apt-common; however:
  Package python-apt-common is not configured yet.
dpkg: error processing python-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-common:
 language-selector-common depends on python2.7; however:
  Package python2.7 is not configured yet.
 language-selector-common depNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
   ends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 language-selector-common depends on python (<< 2.8); however:
  Package python is not configured yet.
 language-selector-common depends on python-apt (>= 0.7.12.0); however:
  Package python-apt is not configured yet.
dpkg: error processing language-selector-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-release:
 lsb-release depends on python2.7; however:
  Package python2.7 is not configured yet.
 lsb-release depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 lsb-release depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing lsb-release (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python2.7; however:
  Package python2.7 is not configured yet.
 update-manager-core depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 update-manager-core depends on python (<< 2.8); however:
  Package python is not configured yet.
 update-manager-core depends on python-apt (>= 0.7.13.4ubuntu3); however:
  Package python-apt is not configured yet.
 update-manager-core depends on lsb-release; however:
  Package lsb-release is not configured yet.
dpkg: error processing update-manager-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-problem-report:
 python-problem-report depends on python2.7; however:
  Package python2.7 is not configured yet.
 python-problem-report depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-problem-report depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-problem-report (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python2.7; however:
  Package python2.7 is not configured yet.
 python-apport depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-apport depends on python (<< 2.8); however:
  Package python is not configured yet.
 python-apport depends on python-apt (>= 0.7.9); however:
  Package python-apt is not configured yet.
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.
 python-apport depends on lsb-release; however:
  Package lsb-release is not configured yet.
dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python (>= 2.6); however:
  Package python is not configured yet.
 apport depends on python-apport (>= 2.0.1-0ubuntu17.6); however:
  Package python-apport is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apt-xapian-index:
 apt-xapian-index depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 apt-xapian-index depends on python-apt (>= 0.7.93.2); however:
  Package python-apt is not configured yet.
 apt-xapian-index depends on python2.7; however:
  Package python2.7 is not configured yet.
 apt-xapian-index depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing apt-xapian-index (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of landscape-common:
 landscape-common depends on python2.7; however:
  Package python2.7 is not configured yet.
 landscape-common depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 landscape-common depends on python (<< 2.8); however:
  Package python is not configured yet.
 landscape-common depends on python-apt; however:
  Package python-apt is not configured yet.
 landscape-common depends on lsb-release; however:
  Package lsb-release is not configured yet.
dpkg: error processing landscape-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server-5.5 (5.5.35-0ubuntu0.12.04.2) breaks mysql-server (<< 5.5.35-0ubuntu0.12.04.2) and is installed.
  Version of mysql-server to be configured is 5.5.35-0ubuntu0.12.04.1.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-httplib2:
 python-httplib2 depends on python2.7; however:
  Package python2.7 is not configured yet.
 python-httplib2 depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-httplib2 depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-httplib2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-lazr.restfulclient:
 python-lazr.restfulclient depends on python2.7; however:
  Package python2.7 is not configured yet.
 python-lazr.restfulclient depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-lazr.restfulclient depends on python (<< 2.8); however:
  Package python is not configured yet.
 python-lazr.restfulclient depends on python-httplib2; however:
  Package python-httplib2 is not configured yet.
dpkg: error processing python-lazr.restfulclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-openssl:
 python-openssl depends on python2.7; however:
  Package python2.7 is not configured yet.
 python-openssl depends on python (>= 2.7.1-0ubuntu2); however:
  Package python is not configured yet.
 python-openssl depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-openssl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.7
 libpython2.7
 python
 apparmor
 python-apt-common
 python-apt
 language-selector-common
 lsb-release
 update-manager-core
 python-problem-report
 python-apport
 apport
 apt-xapian-index
 landscape-common
 mysql-server
 python-httplib2
 python-lazr.restfulclient
 python-openssl
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ian-weisser on 2014-03-19
Whew. You've had this problem a while, I see.

I see this problem (Python can't be upgraded) most often with a mangled /etc/apt/sources.list, and with PPAs.
It's very rare to see an Ubuntu Repsitory package requiring a single version (not upgradable) of software, but it's common among PPAs.

Disable all your PPAs, third-party repositories, and other non-Ubuntu software. Don't delete them. Just disable them.
Then clean out your /var/cache/apt/archives using the *apt-get clean* command to remove uninstalled-but-downloaded non-Ubuntu packages.
Then try updating and upgrading again.

---

### Post by grahammechanical on 2014-03-19
Did you do this?

> [COLOR=#000000]You might want to run 'apt-get -f install' to correct these.[/COLOR]

---

### Post by isac630728 on 2014-03-30
yes I did try apt-get -f install and i still got the same errors (you can see the errors in my first post). Anyway it was related to a snmp package. One of the SNMP package un-installation was corrupt. I created a file "snmp.conf" and then apt-get remove snmp. Then I was able to upgrade or remove anything.

---

### Post by bapoumba on 2014-03-30
Good to see you fixed it. Please mark your thread as solved (under Thread Tools), thanks!

---

