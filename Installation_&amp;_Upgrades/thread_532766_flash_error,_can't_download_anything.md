---
title: "flash error, can't download anything"
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by Devile on 2007-08-23
> matt@matt-laptop:~$ sudo apt-get update
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Ign [http://www.politicalcrossfire.com](http://www.politicalcrossfire.com) dapper Release.gpg
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release
Get:3 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release.gpg [307B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://www.politicalcrossfire.com](http://www.politicalcrossfire.com) dapper Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://www.politicalcrossfire.com](http://www.politicalcrossfire.com) dapper/main Packages
Get:7 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release [23.7kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Get:8 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas/all Packages [19.9kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 43.9kB in 1s (28.5kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
matt@matt-laptop:~$ sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-2.6.15-28-686 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Setting up flashplugin-nonfree (9.0.21.78~ubuntu1~dapper1) ...
Downloading... download failed
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bumps-multimedia:
 bumps-multimedia depends on flashplugin-nonfree; however:
  Package flashplugin-nonfree is not configured yet.
dpkg: error processing bumps-multimedia (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 flashplugin-nonfree
 bumps-multimedia
E: Sub-process /usr/bin/dpkg returned an error code (1)
matt@matt-laptop:~$


trying to update and all it won't let me...

---

### Post by heimo on 2007-08-23
First thing you should do is remove duplicate entries from sources.list. Run apt-get update after that. Then you could try uninstalling conflicting packages and then reinstalling those.
```
sudo apt-get --purge remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

---

