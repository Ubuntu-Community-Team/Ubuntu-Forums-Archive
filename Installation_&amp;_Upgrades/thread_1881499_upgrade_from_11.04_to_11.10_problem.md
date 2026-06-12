---
title: "upgrade from 11.04 to 11.10 problem"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by LockDog on 2011-11-15
Hi All!
I upgraded Ubuntu from 11.04 to 11.10 and now all works but in software manager i can't install\uninstall programs.
Ubuntu can't repairs dependencies, error is:

nstallArchives()  failed: (Reading database ...  (Reading database ... 5% (Reading  database ... 10% (Reading database ... 15% (Reading database ... 20%  (Reading database ... 25% (Reading database ... 30% (Reading database  ... 35% (Reading database ... 40% (Reading database ... 45% (Reading  database ... 50% (Reading database ... 55% (Reading database ... 60%  (Reading database ... 65% (Reading database ... 70% (Reading database  ... 75% (Reading database ... 80% (Reading database ... 85% (Reading  database ... 90% (Reading database ... 95% (Reading database ... 100%  (Reading database ... 196216 files and directories currently installed.)
Unpacking libbrasero-media3-1 (from .../libbrasero-media3-1_3.2.0-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libbrasero-media3-1_3.2.0-0ubuntu1_amd64.deb (--unpack):
corrupted filesystem tarfile - corrupted package archive
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
/var/cache/apt/archives/libbrasero-media3-1_3.2.0-0ubuntu1_amd64.deb
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
dpkg: dependency problems prevent configuration of brasero:
brasero depends on libbrasero-media3-1 (= 3.2.0-0ubuntu1); however:
 Package libbrasero-media3-1 is not installed.
dpkg: error processing brasero (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of brasero-cdrkit:
brasero-cdrkit depends on libbrasero-media3-1 (= 3.2.0-0ubuntu1); however:
 Package libbrasero-media3-1 is not installed.
dpkg: error processing brasero-cdrkit (--configure):
dependency problems - leaving unconfigured

How can i fix it? 
Please help

---

### Post by bluexrider on 2011-11-15
From the terminal:

sudo apt-get -f dist-upgrade

---

### Post by LockDog on 2011-11-15
lockdog@ubuntu:~$ sudo apt-get -f dist-upgrade
[sudo] password for lockdog: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following NEW packages will be installed
  libbrasero-media3-1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/472 kB of archives.
After this operation, 1,815 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 196216 files and directories currently installed.)
Unpacking libbrasero-media3-1 (from .../libbrasero-media3-1_3.2.0-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libbrasero-media3-1_3.2.0-0ubuntu1_amd64.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libbrasero-media3-1_3.2.0-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
lockdog@ubuntu:~$

---

### Post by bluexrider on 2011-11-15
The problem is libbrasero-media3-1_3.2.0-0ubuntu1_amd64.deb

Note that for safety reason, please backup those files that I defined below.




First Delete (sudo rm)


/var/cache/apt/archives/**libbrasero-media3-1_3.2.0-0ubuntu1_amd64.deb**


After that, type this following codes respectively on the terminal.[INDENT]sudo apt-get clean all
[/INDENT][INDENT]sudo apt-get  update //run it twice
[/INDENT][INDENT]sudo apt-get upgrade
[/INDENT]

---

### Post by LockDog on 2011-11-15
[B]bluexrider
[/B]thanx, problem is solved

---

### Post by bluexrider on 2011-11-15
You are welcome

---

