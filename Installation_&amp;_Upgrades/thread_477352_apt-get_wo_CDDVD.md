---
title: "apt-get w/o CD/DVD?"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by LVDave on 2007-06-18
I have a system I've recently switched from Mandrake 9 to Ubuntu 7.04 via clean install.. This is a remote system that I'm trying to configure via ssh and webmin. The system was pretty much set up as needed during the original installation, but now I'm finding I need additional tools such as subversion,  so via ssh I did an "sudo apt-get install subversion" and I get prompted to insert the CD?? The system has an internet connection, and I don't recall being prompted to insert the CD when installing some other stuff a few days ago.. The problem is the system is 70 miles away, and already has a CDRW disk that is needed for backup, in the only CD drive. Is there a way to configure the /etc/apt/sources.list to get everything from repos rather than this??

LVDave

---

### Post by RaZer0r on 2007-06-18
yes this is possible, as you menioned, just remove the lines where cdrom is in :p
do an apt-get update again, and there you are, no more asking for cdroms ;)

---

### Post by LVDave on 2007-06-18
Thank you... 

LVDave

---

