---
title: "synaptic broken because python3 is hosed."
date: 2019-02-18
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2019-02-18
while attempting to reinstall parted (common util)

```
(Reading database ... 216405 files and directories currently installed.)
Preparing to unpack .../parted_3.2-20ubuntu0.1_amd64.deb ...
Unpacking parted (3.2-20ubuntu0.1) over (3.2-20ubuntu0.1) ...
Setting up python3 (3.6.7-1~18.04) ...
running python rtupdate hooks for python3.6...
E: py3compile:183: cannot create directory /usr/share/hplip/ui5/__pycache__: FileNotFoundError(2, 'No such file or directory')
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aboutdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aboutdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aligndialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aligndialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/wifisetupdialog_base.py'
....
error running python rtupdate hook hplip-data
dpkg: error processing package python3 (--configure):
 installed python3 package post-installation script subprocess returned error exit status 4
dpkg: dependency problems prevent configuration of python3-brlapi:
 python3-brlapi depends on python3 (<< 3.7); however:
  Package python3 is not configured yet.
 python3-brlapi depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.
 python3-brlapi depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-brlapi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-dev:
 python3-dev depends on python3 (= 3.6.7-1~18.04); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-dev (--configure):
 dependency prNo apport report written because the error message indicates its a followup error from a previous failure.
                                        No apport report written because the error message indicates its a followup error from a previous failure.
                                                                  No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                              oblems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:
 ubuntu-release-upgrader-core depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
```
....

Attempted to reinstall python3 files
ran the below: 
```
sudo rm -rvf /var/lib/apt/lists/*
sudo apt update
```

What would be the steps to repair python3?
How  or why is hplip involved?

---

### Post by deadflowr on 2019-02-18
Looks like this issue:
[https://ubuntuforums.org/showthread.php?t=2406825]("https://ubuntuforums.org/showthread.php?t=2406825")

---

### Post by pjmlmas on 2019-02-20
Thanks. Looking better.

---

