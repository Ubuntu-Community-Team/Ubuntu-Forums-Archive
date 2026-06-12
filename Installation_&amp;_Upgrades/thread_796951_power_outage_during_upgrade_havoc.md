---
title: "power outage during upgrade havoc"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by eosyn on 2008-05-16
Hi, I was upgrading the system to the latest ubuntu when my laptop lost power (I Have a shot battery) and now I have a bit of trouble starting it up again.
The problem seems to be in cupsys-client and a 'newline missing' I get..

# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  cupsys-bsd: Depends: cupsys-client (= 1.3.7-1ubuntu3) but 1.3.2-1ubuntu7.6 is installed
E: Unmet dependencies. Try using -f.


then I try to do apt-get -f install and the results:

~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libneon25
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cupsys-client
Suggested packages:
  cupsys-pt gtklp kdeprint xpp
The following packages will be upgraded:
  cupsys-client
1 upgraded, 0 newly installed, 0 to remove and 531 not upgraded.
1 not fully installed or removed.
Need to get 0B/125kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/cupsys-client_1.3.7-1ubuntu3_i386.deb (--unpack):
 files list file for package `libgutenprint2' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/cupsys-client_1.3.7-1ubuntu3_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@northstar:~# 

I've rm'd the offending .deb and tried to reinstall but to no avail it fails every time and seems to be holding up the upgrade process.

Does anyone know how to get this .deb to be happy again?
Thanks :D

---

### Post by Partyboi2 on 2008-05-17
try [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=12737")

---

