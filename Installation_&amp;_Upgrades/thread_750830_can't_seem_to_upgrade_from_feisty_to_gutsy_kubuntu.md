---
title: "can't seem to upgrade from feisty to gutsy kubuntu"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by bturrie on 2008-04-09
I've been trying to upgrade from feisty to gutsy this evening. The upgrade manager says "could not verify the integrity of the upgrade manager" and the exited. I went into Konsole to take a look. I did

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update 

that produced this

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release [50.9kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release [57.2kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [121kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release [50.9kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages [6341B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages [79.5kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages [6099B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages [91.7kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Packages [12.7kB]
Fetched 477kB in 2s (191kB/s)
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems

I have no idea what this means but assume it's related to the integrity bit above. Anyone have any suggestions?

SOLVED I'd had to reset my bios and my system clock was several years out of date. as soon as I set the clock the upgrade manager was happy.

---

### Post by zvacet on 2008-04-10
Do you have all repos open?If you don´t go to the Kmenu>system>Adept>Manage Repositories>check all boxes under Ubuntu software and under updates tab.Relopad.

```
sudo apt-get update && sudo apt-get upgrade
```

---

