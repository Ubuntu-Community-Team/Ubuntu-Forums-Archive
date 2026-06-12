---
title: "can not upgrade"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by faziz on 2008-10-20
Hey Guys

I am having problems getting an upgrade.

I am getting 

dpkg: parse error, in file `/var/lib/dpkg/status' near line 24852 package `libsasl2-modules-otp':
 error in Version string `2048:': nothing after colon in version number
E: Sub-process /usr/bin/dpkg returned an error code (2)


when apt-get upgrade.

Thanks
Faisal

---

### Post by Ryadt on 2008-10-20
What happens if you do ```
sudo apt-get update
```

---

### Post by Sef on 2008-10-20
What are you upgrading to and from?

---

### Post by faziz on 2008-10-27
sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy Release
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy-updates Release
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy/main Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy/restricted Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy/main Sources
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy/restricted Sources
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy/universe Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy/universe Sources
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done

---

### Post by faziz on 2008-10-27
What are you upgrading to and from?

I am running regular upgade through the internet. Is that what you were asking?

---

### Post by Pumalite on 2008-10-27
sudo apt-get update
sudo apt-get dist-upgrade

Only then start thinking of upgrading. Here is a link to it:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by faziz on 2008-10-27
even after dist-upgrade I am still getting 

...
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 24852 package `libsasl2-modules-otp':
 error in Version string `2048:': nothing after colon in version number
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

