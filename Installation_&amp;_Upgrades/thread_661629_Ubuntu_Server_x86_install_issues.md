---
title: "Ubuntu Server x86 install issues"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by isoprophlex0 on 2008-01-08
Ubuntu 64 bit edition 7.10 Gutsy


Hello all; I'm having the following issues;

1. Using "apt-get install ubuntu-desktop" I am unable to obtain ubuntu-desktop. Below is what occurs...

I have altered the sources.list file to ftp.iinet.net.au as this is my current ISP and they host Ubuntu.

I have also updated apt-get successfully via apt-get update (as per below)

Any sugestions?

Many thanks :)



```

root@ubuntu:/etc/apt# apt-get update
Ign cdrom://Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_AU
Ign cdrom://Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_AU
Get:1 http://ftp.iinet.net.au gutsy Release.gpg [191B]
Ign http://ftp.iinet.net.au gutsy/universe Translation-en_AU
Get:2 http://ftp.iinet.net.au gutsy Release.gpg [191B]
Ign http://ftp.iinet.net.au gutsy/multiverse Translation-en_AU
Get:3 http://ftp.iinet.net.au gutsy-updates Release.gpg [191B]
Ign http://ftp.iinet.net.au gutsy-updates/universe Translation-en_AU
Ign http://ftp.iinet.net.au gutsy-updates/multiverse Translation-en_AU
Get:4 http://ftp.iinet.net.au gutsy-backports Release.gpg [191B]
Ign http://ftp.iinet.net.au gutsy-backports/main Translation-en_AU
Ign http://ftp.iinet.net.au gutsy-backports/restricted Translation-en_AU
Ign http://ftp.iinet.net.au gutsy-backports/universe Translation-en_AU
Ign http://ftp.iinet.net.au gutsy-backports/multiverse Translation-en_AU
Get:5 http://ftp.iinet.net.au gutsy Release [65.9kB]
Get:6 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_AU
Get:7 http://archive.canonical.com gutsy Release.gpg [191B]
Ign http://archive.canonical.com gutsy/partner Translation-en_AU
Get:8 http://ftp.iinet.net.au gutsy Release [65.9kB]
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_AU
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_AU
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_AU
Hit http://archive.canonical.com gutsy Release
Get:9 http://ftp.iinet.net.au gutsy-updates Release [58.5kB]
Get:10 http://ftp.iinet.net.au gutsy-backports Release [44.0kB]
Get:11 http://ftp.iinet.net.au gutsy/universe Packages [4007kB]
Hit http://security.ubuntu.com gutsy-security Release
Hit http://archive.canonical.com gutsy/partner Packages
Hit http://archive.canonical.com gutsy/partner Sources
Hit http://security.ubuntu.com gutsy-security/main Packages
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Get:12 http://ftp.iinet.net.au gutsy/universe Sources [1226kB]
Get:13 http://ftp.iinet.net.au gutsy/multiverse Packages [152kB]
Get:14 http://ftp.iinet.net.au gutsy/multiverse Sources [56.8kB]
Get:15 http://ftp.iinet.net.au gutsy-updates/universe Packages [43.8kB]
Get:16 http://ftp.iinet.net.au gutsy-updates/universe Sources [7794B]
Get:17 http://ftp.iinet.net.au gutsy-updates/multiverse Packages [9226B]
Get:18 http://ftp.iinet.net.au gutsy-updates/multiverse Sources [1702B]
Get:19 http://ftp.iinet.net.au gutsy-backports/main Packages [14.8kB]
Get:20 http://ftp.iinet.net.au gutsy-backports/restricted Packages [14B]
Get:21 http://ftp.iinet.net.au gutsy-backports/universe Packages [54.4kB]
Get:22 http://ftp.iinet.net.au gutsy-backports/multiverse Packages [3175B]
Get:23 http://ftp.iinet.net.au gutsy-backports/main Sources [5619B]
Get:24 http://ftp.iinet.net.au gutsy-backports/restricted Sources [14B]
Get:25 http://ftp.iinet.net.au gutsy-backports/universe Sources [10.5kB]
Get:26 http://ftp.iinet.net.au gutsy-backports/multiverse Sources [1379B]
Fetched 5828kB in 11s (506kB/s)
Reading package lists... Done
root@ubuntu:/etc/apt# apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntu-desktop


```

---

