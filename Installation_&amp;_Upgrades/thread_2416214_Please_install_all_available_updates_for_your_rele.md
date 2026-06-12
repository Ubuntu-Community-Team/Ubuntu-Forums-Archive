---
title: "Please install all available updates for your release before"
date: 2019-04-07
forum: Installation &amp; Upgrades
---

### Post by bobptz on 2019-04-07
Hello

I am trying to upgrade Ubuntu from 16.04 to 18.04.

First I try to run a normal update, so that later I can click on the upgrade button.

I saw this message:
```
waiting for unattended-upgr to exit
```

I pressed ESC and tried again.  This is the message I get:
```
$ sudo do-release-upgrade
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.
```

Somebody suggested these commands, but it still failed:
```
$ sudo apt-get update
[sudo] password for bob: 
Hit:1 http://download.virtualbox.org/virtualbox/debian xenial InRelease
Hit:2 http://ppa.launchpad.net/nemh/systemback/ubuntu xenial InRelease         
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [109 kB]     
Hit:4 http://gr.archive.ubuntu.com/ubuntu xenial InRelease                     
Hit:5 http://linux.teamviewer.com/deb stable InRelease                         
Get:6 http://gr.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]    
Hit:7 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial InRelease           
Hit:8 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:9 https://repo.skype.com/deb stable InRelease                              
Hit:10 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease       
Get:11 http://gr.archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB] 
Fetched 325 kB in 0s (373 kB/s)                               
Reading package lists... Done
bob@bob-i5-dell:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  va-driver-all
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
bob@bob-i5-dell:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  va-driver-all
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
bob@bob-i5-dell:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
bob@bob-i5-dell:~$ sudo apt-get clean
bob@bob-i5-dell:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.
bob@bob-i5-dell:~$ 


```

---

### Post by westie457 on 2019-04-07
Give this a try
```
 sudo apt install va-driver-all
sudo apt update
sudo apt do-release-upgrade
``` Let us know what happens.

---

### Post by bobptz on 2019-04-07
Hi

Yes, the problem was the "va-driver-all".  This fixed the problem:

> sudo apt-get purge va-driver-all

---

### Post by inperfect on 2020-02-24
Just for the record.

The solution is basically install/purge all the packages listed after

```
The following packages have been kept back:
   name_of_package1 name_of_package_2

```

That is: 

```
sudo apt-get install name_of_package1 name_of_package_2.....
```

Then perform the regular comands for distro upgrade:
```
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
sudo apt install do-release-upgrade 
```

(the last in case the "do-release-upgrade" tool is not installed) and

```
sudo do-release-upgrade
```

I had a different list of packages, and after installing them the problem was (of course) solved too (not any other comand receipe "tutorials" worked). 

Thank you westie457!

---

### Post by wildmanne39 on 2020-02-24
Old thread back to sleep.

---

