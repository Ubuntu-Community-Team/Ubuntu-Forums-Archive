---
title: "can't open the update manager and synoptic manager"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by PeterKogler on 2010-08-14
can't open synaptic package manager and update manager.
The error message I get is:
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing modemmanager (NewVersion1), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'

I posted this problem before but the commands I was given didn't work.
The text i received was:
peter@peter-laptop:~$ sudo killall synaptic && sudo killall  aptitude && sudo killall mintinstall && sudo killall  software-center
[sudo] password for peter: 
synaptic: no process found
peter@peter-laptop:~$ sudo killall synaptic && sudo killall  aptitude && sudo killall mintinstall && sudo killall  software-center
synaptic: no process found
peter@peter-laptop:~$ sudo rm /var/lib/dpkg/lock && sudo rm  /var/cache/apt/archives/lock && sudo rm  /var/lib/apt/lists/partial/* && sudo rm /var/cache/apt/*.bin 
peter@peter-laptop:~$ sudo dpkg --purge $(dpkg -l |grep  ^rc |awk  '{print $2}' | tr '\012' ' ') 
dpkg-query: parse error, in file '/var/lib/dpkg/status' near line 6261  package 'modemmanager':
 `Depends' field, syntax error after reference to package `libgudev-1.0'
dpkg: parse error, in file '/var/lib/dpkg/status' near line 6261 package  'modemmanager':
 `Depends' field, syntax error after reference to package `libgudev-1.0'
peter@peter-laptop:~$ sudo apt-get -f install && sudo apt-get  clean && sudo apt-get autoclean 
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing modemmanager (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
peter@peter-laptop:~$ sudo apt-get autoremove && sudo apt-get  update && sudo apt-get --fix-broken upgrade

the other command I was given gave the same result:
peter@peter-laptop:~$ sudo apt-get -f install
[sudo] password for peter: 
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing modemmanager (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
peter@peter-laptop:~$ 

How can I solve this?
Thankful for all help.
Bless // Peter

---

