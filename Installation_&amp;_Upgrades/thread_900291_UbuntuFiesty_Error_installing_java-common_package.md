---
title: "Ubuntu:Fiesty: Error installing java-common package"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by dipaktc on 2008-08-25
I have power pc machine on which I have installed Ubuntu Fiesty.
I tried installing java-common package and I got an error while installing gij. Here is the log. Can someone help me with this. I get the same error when I try to install gnome-desktop-data too.

I see an illegal instruction while setting up gij-4.1 (4.1.2-0ubuntu5) ...

root@(none):~# apt-get install java-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
java-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gij-4.1 (4.1.2-0ubuntu5) ...
[SIZE="3"]**Illegal instruction**[/SIZE]
dpkg: error processing gij-4.1 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gij:
 gij depends on gij-4.1 (>= 4.1.2); however:
  Package gij-4.1 is not configured yet.
dpkg: error processing gij (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsvn-java:
 libsvn-java depends on gij | java2-runtime; however:
  Package gij is not configured yet.
  Package java2-runtime is not installed.
  Package gij which provides java2-runtime is not configured yet.
  Package gij-4.1 which provides java2-runtime is not configured yet.
dpkg: error processing libsvn-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsvn-javahl:
 libsvn-javahl depends on libsvn-java; however:
  Package libsvn-java is not configured yet.
dpkg: error processing libsvn-javahl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gij-4.1
 gij
 libsvn-java
 libsvn-javahl
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@(none):~#

---

### Post by Bablefish on 2008-08-25
Did you try going through add remove? You will find Java there.

---

### Post by dipaktc on 2008-08-25
I removed gij-4.1 and tried installing the required packages again. It worked.
Thanks for the reply.

---

