---
title: "Multiple warnings/errors with package update"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by Jessehk on 2006-07-02
Using the sources.list found here: [http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php) , I get multiple errors when attempting to update using the command-line mode of aptitude and apt-get. 

They go away when I run update again, but I'd really appreciate help on why they are occurring every time I update after logging in.

**my update output**
```

$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release [30.9kB]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [30.9kB]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [19.6kB]
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [26.4kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/universe Packages [8592B]
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [38.0kB]
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4253B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [6774B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [6042B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [22.4kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [14B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [14B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [902B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [6042B]
99% [25 Packages bzip2 0]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages - open (2 No such file or directory)
Fetched 234kB in 1s (144kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```


Any help would be really appreciated. Thanks :)

---

