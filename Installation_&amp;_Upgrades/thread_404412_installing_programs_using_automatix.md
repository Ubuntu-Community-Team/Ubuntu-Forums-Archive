---
title: "installing programs using automatix"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by peterbug on 2007-04-08
ok I have automatix installed and running but I cannot download any software from it, whenever I try to download frost wire for example I get an error message telling me that ¨An apt-based error occurred and installation was unsuccessful¨ this occurs for all software I tried to download Im just using frost wire as an example. 

when I type 

¨sudo apt-get update¨

I receive the following :


Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Translation-en_US
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Get:8 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Fetched 8B in 4m0s (0B/s)
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/Release.gpg](http://www.getautomatix.com/apt/dists/edgy/Release.gpg)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2](http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

can anyone tell me why things wont install?

---

### Post by aysiu on 2007-04-08
I think it should be obvious--it can connect to just about all the legitimate Ubuntu and Canonical repositories, but it can't connect to the Automatix server: ```
Failed to fetch http://www.getautomatix.com/apt/dists/edgy/Release.gpg Could not connect to www.getautomatix.com:80 (1.0.0.0), connection timed out
``` Over the past couple of months, [the Automatix server has been up and down and up and down again.](http://ubuntuforums.org/showthread.php?t=368839)

You have a couple of other alternatives.

**Automated**
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

**Manual**
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by peterbug on 2007-04-08
yes but I dont see why that should effect whether or not I can download software using automatix seeing as automatix is already properly installed?

---

### Post by blackened on 2007-04-08
The ignores I'm not sure about, but the connection failures are because of automatix's flaky servers. Sometimes they're up, sometimes they're down, sometimes they're flooded and are unavailable due to high traffic. 
**Edit:**Ack, ADD gets the better of me once again. Opened a reply window and got distracted.

---

### Post by peterbug on 2007-04-08
so basically leave it and try again later? =P

---

### Post by zvacet on 2007-04-08
No,try to find another way to download and install programs you want.If you don´t know how to do it just ask.

---

### Post by aysiu on 2007-04-08
> **zvacet said:**
> If you don´t know how to do it just ask. Or read the second post in this thread.

---

