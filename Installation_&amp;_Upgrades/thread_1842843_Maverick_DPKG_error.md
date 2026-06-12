---
title: "Maverick DPKG error"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by abhinavnain on 2011-09-12
hey well um a newbie to UBUNTU but i know how to install software/packages using LINUX TERMINAL by apt-get but from past few days whenever I try to do so the following error shows up ..
*This was when I tried to install SKYPE*

root@ubuntu:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  skype
0 upgraded, 1 newly installed, 0 to remove and 293 not upgraded.
11 not fully installed or removed.
Need to get 23.6MB of archives.
After this operation, 29.9MB of additional disk space will be used.
Get:1 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner skype i386 2.2.0.35-0maverick1 [23.6MB]
Fetched 23.6MB in 6min 35s (59.6kB/s)                                          
Setting up tar (1.23-2ubuntu2) ...
update-alternatives: error: cannot append to /usr/local/var/log/alternatives.log : No such file or directory
dpkg: error processing tar (--configure): subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 tar
E: Sub-process /usr/bin/dpkg returned an error code (1)

the similar things shows up in synaptic and ubuntu software center also..

---

### Post by howefield on 2011-09-12
Thread closed, duplicate here : [http://ubuntuforums.org/showthread.php?p=11243676#post11243676](http://ubuntuforums.org/showthread.php?p=11243676#post11243676)

---

