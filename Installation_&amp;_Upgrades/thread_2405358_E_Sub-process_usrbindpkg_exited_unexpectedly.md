---
title: "E: Sub-process /usr/bin/dpkg exited unexpectedly"
date: 2018-11-04
forum: Installation &amp; Upgrades
---

### Post by sunbear-c22 on 2018-11-04
I was doing a regular `apt update` when and `apt upgrade` on Ubuntu 16.04 but encountered this `dpkg` failure. How do i fix this issue?

```
$ apt list --upgradable
Listing... Done
openshot-qt/xenial,xenial 2.4.3+dfsg2+993+201811032052~ubuntu16.04.1 all [upgradable from: 2.4.3+dfsg2+992+201811022054~ubuntu16.04.1]
openshot-qt-doc/xenial,xenial 2.4.3+dfsg2+993+201811032052~ubuntu16.04.1 all [upgradable from: 2.4.3+dfsg2+992+201811022054~ubuntu16.04.1]
python3-update-manager/xenial-updates,xenial-updates 1:16.04.15 all [upgradable from: 1:16.04.14]
update-manager/xenial-updates,xenial-updates 1:16.04.15 all [upgradable from: 1:16.04.14]
update-manager-core/xenial-updates,xenial-updates 1:16.04.15 all [upgradable from: 1:16.04.14]
sunbear@Eliot:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  openshot-qt openshot-qt-doc python3-update-manager update-manager update-manager-core
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 58.6 MB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://sg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 python3-update-manager all 1:16.04.15 [33.4 kB]
Get:2 http://ppa.launchpad.net/openshot.developers/libopenshot-daily/ubuntu xenial/main amd64 openshot-qt all 2.4.3+dfsg2+993+201811032052~ubuntu16.04.1 [54.3 MB]
Get:3 http://sg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 update-manager-core all 1:16.04.15 [5,498 B]
Get:4 http://sg.archive.ubuntu.com/ubuntu xenial-updates/main amd64 update-manager all 1:16.04.15 [544 kB]
Get:5 http://ppa.launchpad.net/openshot.developers/libopenshot-daily/ubuntu xenial/main amd64 openshot-qt-doc all 2.4.3+dfsg2+993+201811032052~ubuntu16.04.1 [3,706 kB]
Fetched 58.6 MB in 2min 56s (332 kB/s)                                                                                                             
dpkg: ../../src/filesdb.c:595: findnamenode: Assertion `(*pointerp)->name[0] == '/'' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  openshot-qt openshot-qt-doc python3-update-manager update-manager update-manager-core
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/58.6 MB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Segmentation fault
dpkg: ../../src/filesdb.c:595: findnamenode: Assertion `(*pointerp)->name[0] == '/'' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

```

---

