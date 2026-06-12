---
title: "upgrade from 7.10 to 8.04 wont happen"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by ollisiren on 2008-04-27
When running update manager and check it confirms that system is up to date, but even when cheking again it wont suggest the upgrade

and additionally:

*****:~$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

How to fix this?

---

### Post by dstew on 2008-04-27
You can try```
sudo apt-get install update-manager-core
```before you try```
sudo do-release-upgrade
```

---

### Post by vanadium on 2008-04-27
Just have a little patience for one more week or so.

---

### Post by ollisiren on 2008-05-01
dstew: all I get when I try this is:

sudo apt-get install update-manager-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version.
update-manager-core set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

---

### Post by ollisiren on 2008-05-01
or...

sudo aptitude update && sudo aptitude dist-upgrade
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [191B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Fetched 4B in 0s (8B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done    

but still no upgrade...

---

### Post by bone2006 on 2008-05-23
samething on one of the systems I'm on

---

