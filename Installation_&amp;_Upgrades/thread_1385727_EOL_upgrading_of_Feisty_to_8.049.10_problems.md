---
title: "EOL upgrading of Feisty to 8.04/9.10 problems"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by KyPeN on 2010-01-19
Evening all,

I've tried following [this guide]("https://help.ubuntu.com/community/EOLUpgrades/Feisty"), but there seems to be an issue.

I've added the repos to my sources.list file.  It seems to do an apt-get update fine, but upgrading/dist-upgrade does nothing:

```

kypen@Ripley:~$ sudo aptitude update && sudo aptitude upgrade
Get:1 http://old-releases.ubuntu.com feisty Release.gpg [191B]
Ign http://old-releases.ubuntu.com feisty/main Translation-en_US
Ign http://old-releases.ubuntu.com feisty/restricted Translation-en_US
Ign http://old-releases.ubuntu.com feisty/universe Translation-en_US
Ign http://old-releases.ubuntu.com feisty/multiverse Translation-en_US
Get:2 http://old-releases.ubuntu.com feisty-updates Release.gpg [189B]
Ign http://old-releases.ubuntu.com feisty-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com feisty-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com feisty-updates/multiverse Translation-en_US
Get:3 http://old-releases.ubuntu.com feisty-security Release.gpg [189B]
Ign http://old-releases.ubuntu.com feisty-security/main Translation-en_US
Ign http://old-releases.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com feisty-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com feisty Release
Hit http://old-releases.ubuntu.com feisty-updates Release
Hit http://old-releases.ubuntu.com feisty-security Release
Hit http://old-releases.ubuntu.com feisty/main Packages
Hit http://old-releases.ubuntu.com feisty/restricted Packages
Hit http://old-releases.ubuntu.com feisty/universe Packages
Hit http://old-releases.ubuntu.com feisty/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-updates/main Packages
Hit http://old-releases.ubuntu.com feisty-updates/restricted Packages
Hit http://old-releases.ubuntu.com feisty-updates/universe Packages
Hit http://old-releases.ubuntu.com feisty-updates/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-security/main Packages
Hit http://old-releases.ubuntu.com feisty-security/restricted Packages
Hit http://old-releases.ubuntu.com feisty-security/universe Packages
Hit http://old-releases.ubuntu.com feisty-security/multiverse Packages
Fetched 3B in 1s (3B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
kypen@Ripley:~$

```

Does anyone have any suggestions?  

Cheers.

---

### Post by kostkon on 2010-01-19
But to dist-upgrade you need to give
```
sudo aptitude dist-upgrade
```

```
sudo aptiture upgrade
```
just updates the packages.

---

### Post by slakkie on 2010-01-20
Hi, please read the guide, you are not performing all of the instructions. It is a step by step guide, if you follow what is said there you will upgrade your machine properly.

---

