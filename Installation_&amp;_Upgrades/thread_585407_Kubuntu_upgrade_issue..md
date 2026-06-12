---
title: "Kubuntu upgrade issue."
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by AlainJLEB on 2007-10-21
Hi there,

I have tried to upgrade from 7.04 to .10 following the upgrade path. This has worked fine, until it blocked during the version upgrade. During the last point, just before rebooting, it was stucked, and I had to kill the process.

Afterwards, when I try to run adept-manager or adapte-update, they are crashing. apt-get update give the following output:
root@laptop:~# apt-get update
Get:1 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:2 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy Release
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-en_US
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy/main Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy/universe Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy/universe Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy/multiverse Sources
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release [37.0kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages [14B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages [20.4kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages [14B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages [7633B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages
Fetched 65.3kB in 1s (61.0kB/s)
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing apport-retrace (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

There are  a mix of feisty and gutsy ... Any idea on what can be the root cause of the issue, and moreover how to solve it? I would like to avoid full reinstall :(

Thanks
Alain

---

