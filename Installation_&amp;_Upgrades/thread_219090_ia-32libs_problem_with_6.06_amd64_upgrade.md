---
title: "ia-32libs problem with 6.06 amd64 upgrade"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by gdlx on 2006-07-19
used update manager to upgrade to Dapper 6.06. download and upgrade went well until an error with ia32-libs and the upgrade aborted. The system still boots. there is no open-office and synaptic still shows that ia32-libs needs to be upgraded. trying to use synaptic aborts with error and following the 'how-to' offered by Ubuntu-Demon gave the following errors. any help will be greatly appreciated as I cannot do any work without OOo calc.

Terminal:

$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  gnome-cups-manager
The following packages will be upgraded:
  ia32-libs
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B/3837kB of archives.
After unpacking 14.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 109698 files and directories currently installed.)
Preparing to replace ia32-libs 1.4ubuntu4 (using .../ia32-libs_1.4ubuntu19_amd64.deb) ...
dpkg-divert: rename involves overwriting `/usr/bin/ldd' with
  different file `/usr/bin/ldd.amd64', not allowed
dpkg: error processing /var/cache/apt/archives/ia32-libs_1.4ubuntu19_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_1.4ubuntu19_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

NEXT: tried to remove ia32-libs

$ sudo apt-get remove ia32-libs
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  ia32-libs
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 23.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 109696 files and directories currently installed.)
Removing ia32-libs ...
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/bin/ldd to /usr/bin/ldd.ia32-libs by ia32-libs'
  found `diversion of /usr/bin/ldd to /usr/bin/ldd.amd64 by ia32-libs'
dpkg: error processing ia32-libs (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 ia32-libs
E: Sub-process /usr/bin/dpkg returned an error code (1)
$
:confused:

---

### Post by gdlx on 2006-07-20
This is how I solved part of the problem.

 rm /usr/bin/ldd and used synaptic to remove all of ia32-libs and OpenOffice. Then reloaded ia32-libs and OpenOffice. Everything is in place but the new problem is that Open Office doesn't load. 

Anyone have a suggestion?

:(

---

### Post by gdlx on 2006-07-25
Go here for the methods I found most helpful in solving broken dependencies.

[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

This person is very good at explaining the details.

---

