---
title: "Errors were encountered while processing:  icedtea-netx:i386"
date: 2014-11-13
forum: Installation &amp; Upgrades
---

### Post by sajerg281 on 2014-11-13
I am using ubuntumate 14.10 and want to install openjdk-7-jdk using

[B]sudo apt-get install openjdk-7-jdk

[/B]but there is an error and the result is as follows. 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-7-jdk is already the newest version.
The following packages were automatically installed and are no longer required:
  kde-l10n-de kde-l10n-engb libgee2 libibus-1.0-5 libtimezonemap-data libtimezonemap1 liburl-dispatcher1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up icedtea-netx:i386 (1.5.1-1ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: error: alternative path /usr/lib/jvm/java-8-openjdk-i386/jre/bin/javaws doesn't exist
dpkg: error processing package icedtea-netx:i386 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 icedtea-netx:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

using **uname -a  **gives
 Linux borograf 3.16.0-24-generic #32-Ubuntu SMP Tue Oct 28 13:13:18 UTC 2014 i686 i686 i686 GNU/Linux

how can I solve the error? 
I really appreciate your help

---

### Post by sajerg281 on 2014-11-13
I have also tried to install using the ubuntu software center and the result is as follows

installArchives() failed: Selecting previously unselected package openjdk-8-jre:i386. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 239002 files and directories currently installed.) 
Preparing to unpack .../openjdk-8-jre_8u40~b09-1_i386.deb ... 
Unpacking openjdk-8-jre:i386 (8u40~b09-1) ... 
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ... 
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ... 
Processing triggers for mime-support (3.55ubuntu1) ... 
Setting up openjdk-8-jre:i386 (8u40~b09-1) ... 
Setting up icedtea-netx:i386 (1.5.1-1ubuntu1) ... 
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings because link group itweb-settings is broken 
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link 
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings because link group itweb-settings is broken 
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link 
update-alternatives: error: alternative path /usr/lib/jvm/java-8-openjdk-i386/jre/bin/javaws doesn't exist 
dpkg: error processing package icedtea-netx:i386 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Processing triggers for libc-bin (2.19-10ubuntu2) ... 
Errors were encountered while processing: 
 icedtea-netx:i386 
Error in function:  
Setting up icedtea-netx:i386 (1.5.1-1ubuntu1) ... 
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings because link group itweb-settings is broken 
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link 
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings because link group itweb-settings is broken 
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link 
update-alternatives: error: alternative path /usr/lib/jvm/java-8-openjdk-i386/jre/bin/javaws doesn't exist 
dpkg: error processing package icedtea-netx:i386 (--configure): 
 subprocess installed post-installation script returned error exit status 2

---

### Post by sasafrass452 on 2014-11-30
Still not resolved.... Are the devs aware of this issue?

---

### Post by Philip Bawa on 2014-12-10
I believe it's our cmos batteries... I'm working on overriding them altogether with simple memory backup (BIOS/ROM autosave...)

---

### Post by Philip Bawa on 2014-12-10
Solved! 
 1. Install Synaptics:
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
2. Open Synaptics
3. Search for "Iced"
4. Alt/Right click
5. Mark for Complete Removal
6. Repeat until all IcedTea is returned to the goat.

---

