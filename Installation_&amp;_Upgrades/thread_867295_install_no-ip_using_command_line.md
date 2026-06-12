---
title: "install no-ip using command line"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by lil_niles on 2008-07-22
I have scoured the forums and I haven't found a solution to my problem yet. I am remotely using SSH to add no-ip onto my file server. 

This is what i type:
```
sudo apt-get install no-ip
```

the output is this:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package no-ip

```

Next i try this:
```
 sudo apt-get update
```

and i get this:
```
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [189B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_CA
Get:2 http://ca.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://ca.archive.ubuntu.com gutsy/main Translation-en_CA
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_CA
Hit http://security.ubuntu.com gutsy-security Release
Ign http://ca.archive.ubuntu.com gutsy/restricted Translation-en_CA
Get:3 http://ca.archive.ubuntu.com gutsy-updates Release.gpg [189B]
Ign http://ca.archive.ubuntu.com gutsy-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-updates/restricted Translation-en_CA
Hit http://security.ubuntu.com gutsy-security/main Packages
Hit http://ca.archive.ubuntu.com gutsy Release
Hit http://ca.archive.ubuntu.com gutsy-updates Release
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://ca.archive.ubuntu.com gutsy/main Packages
Hit http://ca.archive.ubuntu.com gutsy/restricted Packages
Hit http://ca.archive.ubuntu.com gutsy/main Sources
Hit http://ca.archive.ubuntu.com gutsy/restricted Sources
Hit http://ca.archive.ubuntu.com gutsy-updates/main Packages
Hit http://ca.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://ca.archive.ubuntu.com gutsy-updates/main Sources
Hit http://ca.archive.ubuntu.com gutsy-updates/restricted Sources
Fetched 3B in 1s (2B/s)
Reading package lists... Done

```

then when i try to install again, i get the same message as before saying it can't find the package. This is odd because on my laptop (not my file server) i can find the package using the GUI.

thanks

---

### Post by cpetercarter on 2008-07-22
I think the package is now called noip2.

---

### Post by sisco311 on 2008-07-22
no-ip is in the universe repositories.
to enable the repo edit the source.list:
```
sudo nano /etc/apt/sources.list
```un-comment the univers repos.
(remove the #)
example:
> ## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
**#**deb [http://*XY*]("http://%3Ci%3EXY%3C/i%3E").archive.ubuntu.com/ubuntu/ gusty **universe**
**#**deb-src [http://*XY*]("http://%3Ci%3EXY%3C/i%3E").archive.ubuntu.com/ubuntu/ gusty **universe**
#deb [http://*XY*]("http://%3Ci%3EXY%3C/i%3E").archive.ubuntu.com/ubuntu/ gusty-updates** universe**
**#**deb-src [http://*XY*]("http://%3Ci%3EXY%3C/i%3E").archive.ubuntu.com/ubuntu/ gusty-updates **universe**
-->
> ## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://*XY*]("http://%3ci%3exy%3c/i%3E").archive.ubuntu.com/ubuntu/ gusty **universe**
deb-src [http://*XY*]("http://%3ci%3exy%3c/i%3E").archive.ubuntu.com/ubuntu/ gusty **universe**
deb [http://*XY*]("http://%3ci%3exy%3c/i%3E").archive.ubuntu.com/ubuntu/ gusty-updates** universe**
deb-src [http://*XY*]("http://%3ci%3exy%3c/i%3E").archive.ubuntu.com/ubuntu/ gusty-updates **universe**


Ctrl+o = save
Ctrl+x = exit

then try:
```
sudo apt-get update[FONT=monospace]
[/FONT]sudo apt-get install no-ip
```

---

### Post by sisco311 on 2008-07-22
> **cpetercarter said:**
> I think the package is now called noip2.

> aptitude show no-ip
Package: no-ip
State: xxx
Version: 2.1.7-7ubuntu1
Priority: optional
Section: universe/net
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 32.8k
Depends: noip2
Description: transitional package to noip2
 This dummy package is provided to smooth the upgrade from no-ip to noip2. This
 package can be safely removed.
Homepage: [http://www.no-ip.com](http://www.no-ip.com)


> aptitude show noip2 
Package: noip2
State: xxx
Version: 2.1.7-7ubuntu1
Priority: optional
Section: universe/net
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 238k
Depends: debconf (>= 0.5) | debconf-2.0, libc6 (>= 2.7-1)
Conflicts: no-ip (< 2.1.7-7ubuntu1)
Replaces: no-ip (< 2.1.7-7ubuntu1)
Description: client for dynamic DNS service
 This package provides the No-IP.com Dynamic DNS update client. 
 
 When configured correctly, the client will check the local IP address at a
 given time interval. If it has changed, the client will notify No-IP.com DNS
 servers and update the IP address for your No-IP/No-IP+ host name.
Homepage: [http://www.no-ip.com](http://www.no-ip.com)
:)

---

### Post by lil_niles on 2008-07-23
thank you very much sisco311, your solution solved my problem exactly. problem solved! no-ip is up and running from the repo

---

