---
title: "How do I upgrade to PHP 5.3?"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by rstackhouse on 2010-06-30
I searched this forum and found two similar posts:

[http://ubuntuforums.org/showthread.php?t=1418791&highlight=upgrade+PHP](http://ubuntuforums.org/showthread.php?t=1418791&highlight=upgrade+PHP)

[http://ubuntuforums.org/showthread.php?t=1415953&highlight=upgrade+PHP](http://ubuntuforums.org/showthread.php?t=1415953&highlight=upgrade+PHP)

The first one mentioned getting PHP from dotdeb. So I tried following the instructions over there: [http://www.dotdeb.org/instructions/](http://www.dotdeb.org/instructions/)

But I get the following when I run apt-get upgrade:

> Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://php53.dotdeb.org](http://php53.dotdeb.org) stable Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Ign [http://php53.dotdeb.org](http://php53.dotdeb.org) stable Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Ign [http://php53.dotdeb.org](http://php53.dotdeb.org) stable/all Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Ign [http://php53.dotdeb.org](http://php53.dotdeb.org) stable/all Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Get:1 [http://php53.dotdeb.org](http://php53.dotdeb.org) stable/all Packages [6367B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources

Does the "Ign" mean that the package source was ignored? If so, how do I fix this? Do I need to apt-get remove and apt-get install PHP?

---

