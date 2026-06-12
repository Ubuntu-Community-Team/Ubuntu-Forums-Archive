---
title: "Repository Problems 5.10-&gt;6.06"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by lemonsCC on 2006-06-02
I cannot use the update manager to move to Dapper so I am trying to do this manually.  I changed my repository list to say dapper instead of breezy and got the following errors

```

chris@ubuntu:~$ sudo apt-get update && sudo apt-get dist-upgrade
Password:
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Get:4 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:5 http://security.ubuntu.com dapper-security Release [19.6kB]
Get:6 http://us.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:7 http://archive.ubuntu.com dapper Release [34.8kB]
Get:8 http://us.archive.ubuntu.com dapper Release [34.8kB]
Ign http://packages.freecontrib.org dapper Release.gpg
Ign http://packages.freecontrib.org dapper Release
Ign http://packages.freecontrib.org dapper/free Packages
Get:9 http://security.ubuntu.com dapper-security/main Packages [14B]
Get:10 http://archive.ubuntu.com dapper-backports Release [19.6kB]
Ign http://packages.freecontrib.org dapper/non-free Packages
Get:11 http://us.archive.ubuntu.com dapper-updates Release [23.4kB]
Get:12 http://security.ubuntu.com dapper-security/restricted Packages [14B]
Get:13 http://security.ubuntu.com dapper-security/main Sources [14B]
Get:14 http://security.ubuntu.com dapper-security/restricted Sources [14B]
Ign http://packages.freecontrib.org dapper/free Sources
Ign http://packages.freecontrib.org dapper/non-free Sources
Get:15 http://security.ubuntu.com dapper-security/universe Packages [14B]
Get:16 http://security.ubuntu.com dapper-security/universe Sources [14B]
Get:17 http://archive.ubuntu.com dapper/universe Packages [2458kB]
Err http://packages.freecontrib.org dapper/free Packages
  404 Not Found
Get:18 http://us.archive.ubuntu.com dapper/main Packages [619kB]
Err http://packages.freecontrib.org dapper/non-free Packages
  404 Not Found
Err http://packages.freecontrib.org dapper/free Sources
  404 Not Found
Err http://packages.freecontrib.org dapper/non-free Sources
  404 Not Found
Get:19 http://us.archive.ubuntu.com dapper/restricted Packages [4571B]
Get:20 http://us.archive.ubuntu.com dapper/main Sources [255kB]
Get:21 http://us.archive.ubuntu.com dapper/restricted Sources [1478B]
Get:22 http://us.archive.ubuntu.com dapper-updates/main Packages [5896B]
Get:23 http://us.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:24 http://us.archive.ubuntu.com dapper-updates/main Sources [1681B]
Get:25 http://us.archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get:26 http://archive.ubuntu.com dapper/multiverse Packages [95.2kB]
Get:27 http://archive.ubuntu.com dapper/universe Sources [975kB]
Get:28 http://archive.ubuntu.com dapper/multiverse Sources [46.6kB]
Get:29 http://archive.ubuntu.com dapper-backports/main Packages [14B]
Get:30 http://archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:31 http://archive.ubuntu.com dapper-backports/universe Packages [14B]
Get:32 http://archive.ubuntu.com dapper-backports/multiverse Packages [14B]
Get:33 http://archive.ubuntu.com dapper-backports/main Sources [14B]
Get:34 http://archive.ubuntu.com dapper-backports/restricted Sources [14B]
Get:35 http://archive.ubuntu.com dapper-backports/universe Sources [14B]
Get:36 http://archive.ubuntu.com dapper-backports/multiverse Sources [14B]
Fetched 4596kB in 30s (148kB/s)
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

What can I do to remedy this problem

Thanks

---

### Post by ubuntu_demon on 2006-06-02
First uncomment the non-official repo's.

$sudo gedit /etc/apt/sources.list
$sudo apt-get update
$sudo apt-get dist-upgrade
$sudo apt-get install ubuntu-base ubuntu-desktop

Now you can change your sources.list to include non-official repo's. Here's the one that I recommend : [http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

---

### Post by catlett on 2006-06-02
The "freecontrib" repository hasn't changed to Dapper. Just switch the freecontrib back to breezy.

P.S. This is happening because the freecontrib is not a regular ubuntu repo. Somewhere along the way you must have added it to your list. The guide you used assumes the repository list hasn't been modified since installation. When you changed your list from dapper to breezy you inadvertently entered aURL that doesn't exist i.e. freecontrib dapper.

---

