---
title: "synaptic fails to download package lists"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by snaef on 2006-09-08
Hi,

Im trying to update my system using synaptic.  When I do anupdate on the packages I get this error:

[INDENT][http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Connection failed [IP: 146.137.96.15 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Connection failed [IP: 195.248.90.54 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Connection failed [IP: 146.137.96.15 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Connection failed
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.54 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) Connection failed
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.54 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) Connection failed
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.54 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.15 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) Connection failed
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.54 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) Connection failed
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.15 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) Connection failed
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.15 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:) Connection failed
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[/INDENT]


If I try to do a wget on one of these files it downloads fine.   Any suggestions??

-Scott

---

### Post by snaef on 2006-09-09
Any suggestions on how to proceed with this?  I just finally got nVidia and my network printer working properly and dont want to resort to a re-install.  

I dont understand why apt cant download these files, but any other app (firefox, wget) can.

:confused: 

-Scott

---

