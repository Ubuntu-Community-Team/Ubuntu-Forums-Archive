---
title: "E: The method driver /usr/lib/apt/methods/https could not be found"
date: 2014-08-06
forum: Installation &amp; Upgrades
---

### Post by suyash2 on 2014-08-06
I am new to ubuntu and am badly stuck with this problem. sudo apt-get update fails with following errors:
E: The method driver /usr/lib/apt/methods/https could not be found.

and if I try to install apt-transport-https, I get this error:

sudo apt-get install -f apt-transport-https
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package apt-transport-https

I tried other suggestions mentioned on this page [http://ubuntuforums.org/showthread.php?t=2179538](http://ubuntuforums.org/showthread.php?t=2179538) but to no avail. Some requested output from the posts mentioned on this page are: 

**lsb_release -a**
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise


**uname -a**
Linux vps.mts5.com 3.2.0-37-virtual #58-Ubuntu SMP Thu Jan 24 15:48:03 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**cat /etc/apt/sources.list**
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe


**grep -Rv '#' /etc/apt/sources.list.d**
/etc/apt/sources.list.d/mozillateam-firefox-next-precise.list:deb [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu) precise main
/etc/apt/sources.list.d/mozillateam-firefox-next-precise.list:deb-src [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu) precise main
/etc/apt/sources.list.d/passenger.list:deb [https://oss-binaries.phusionpassenger.com/apt/passenger](https://oss-binaries.phusionpassenger.com/apt/passenger) precise main
/etc/apt/sources.list.d/passenger.list.save:deb [https://oss-binaries.phusionpassenger.com/apt/passenger](https://oss-binaries.phusionpassenger.com/apt/passenger) precise main

I even tried replacing the files as provided in an attachment mentioned in the above mentioned thread link in order to push https inside the apt/methods directory but nothing has helped so far. 
I don't recall anything gone wrong in recent past. How can these problems be fixed? Would highly appreciate any help/pointers.

---

