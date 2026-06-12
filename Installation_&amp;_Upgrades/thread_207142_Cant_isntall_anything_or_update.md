---
title: "Cant isntall anything or update"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by Owdy on 2006-07-01
All repos gives forbidden 403 error. I dont have a clue how to fix this.

```
osku@Koti:~$ sudo apt-get update
Siv http://packages.freecontrib.org breezy Release.gpg
Siv http://archive.ubuntu.com dapper Release.gpg
Siv http://security.ubuntu.com dapper-security Release.gpg
Siv http://download.skype.com stable Release.gpg
Siv http://dtw.silverentertainment.fi gcc34 Release.gpg
Siv http://fi.archive.ubuntu.com dapper Release.gpg
Siv http://packages.freecontrib.org breezy Release
Siv http://archive.ubuntu.com dapper-backports Release.gpg
Siv http://security.ubuntu.com dapper-security Release
Siv http://download.skype.com stable Release
Siv http://dtw.silverentertainment.fi gcc34 Release
Siv http://fi.archive.ubuntu.com dapper-updates Release.gpg
Siv http://packages.freecontrib.org breezy/free Packages
Siv http://archive.ubuntu.com dapper Release
Siv http://security.ubuntu.com dapper-security/main Packages
Siv http://download.skype.com stable/non-free Packages
Siv http://dtw.silverentertainment.fi gcc34/non-free Packages
Siv http://fi.archive.ubuntu.com dapper Release
Siv http://packages.freecontrib.org breezy/non-free Packages
Siv http://archive.ubuntu.com dapper-backports Release
Siv http://security.ubuntu.com dapper-security/restricted Packages
Vrhe http://download.skype.com stable/non-free Packages
  403 Forbidden
Vrhe http://dtw.silverentertainment.fi gcc34/non-free Packages
  403 Forbidden
Siv http://fi.archive.ubuntu.com dapper-updates Release
Siv http://packages.freecontrib.org breezy/free Sources
Siv http://archive.ubuntu.com dapper/universe Packages
Siv http://security.ubuntu.com dapper-security/main Sources
Siv http://fi.archive.ubuntu.com dapper/main Sources
Siv http://archive.ubuntu.com dapper/multiverse Packages
Siv http://packages.freecontrib.org breezy/non-free Sources
Siv http://security.ubuntu.com dapper-security/restricted Sources
Siv http://fi.archive.ubuntu.com dapper/restricted Sources
Siv http://archive.ubuntu.com dapper/main Packages
Vrhe http://packages.freecontrib.org breezy/free Packages
  403 Forbidden
Siv http://security.ubuntu.com dapper-security/universe Packages
Siv http://fi.archive.ubuntu.com dapper/universe Sources
Siv http://archive.ubuntu.com dapper/restricted Packages
Vrhe http://packages.freecontrib.org breezy/non-free Packages
  403 Forbidden
Siv http://security.ubuntu.com dapper-security/universe Sources
Siv http://fi.archive.ubuntu.com dapper/multiverse Sources
Siv http://archive.ubuntu.com dapper-backports/main Packages
Vrhe http://packages.freecontrib.org breezy/free Sources
  403 Forbidden
Vrhe http://security.ubuntu.com dapper-security/main Packages
  403 Forbidden
Siv http://fi.archive.ubuntu.com dapper-updates/main Packages
Siv http://archive.ubuntu.com dapper-backports/universe Packages
Vrhe http://packages.freecontrib.org breezy/non-free Sources
  403 Forbidden
Vrhe http://security.ubuntu.com dapper-security/restricted Packages
  403 Forbidden
Siv http://fi.archive.ubuntu.com dapper-updates/restricted Packages
Siv http://archive.ubuntu.com dapper-backports/multiverse Packages
Vrhe http://security.ubuntu.com dapper-security/main Sources
  403 Forbidden
Siv http://fi.archive.ubuntu.com dapper-updates/main Sources
Siv http://archive.ubuntu.com dapper-backports/restricted Packages
Vrhe http://security.ubuntu.com dapper-security/restricted Sources
  403 Forbidden
Siv http://fi.archive.ubuntu.com dapper-updates/restricted Sources
Vrhe http://archive.ubuntu.com dapper/universe Packages
  403 Forbidden
Vrhe http://security.ubuntu.com dapper-security/universe Packages
  403 Forbidden
Vrhe http://fi.archive.ubuntu.com dapper/main Sources
  403 Forbidden
Vrhe http://archive.ubuntu.com dapper/multiverse Packages
  403 Forbidden
Vrhe http://security.ubuntu.com dapper-security/universe Sources
  403 Forbidden
Vrhe http://fi.archive.ubuntu.com dapper/restricted Sources
  403 Forbidden
Vrhe http://archive.ubuntu.com dapper/main Packages
  403 Forbidden
Vrhe http://fi.archive.ubuntu.com dapper/universe Sources
  403 Forbidden
Vrhe http://archive.ubuntu.com dapper/restricted Packages
  403 Forbidden
Vrhe http://fi.archive.ubuntu.com dapper/multiverse Sources
  403 Forbidden
Vrhe http://archive.ubuntu.com dapper-backports/main Packages
  403 Forbidden
Vrhe http://fi.archive.ubuntu.com dapper-updates/main Packages
  403 Forbidden
Vrhe http://archive.ubuntu.com dapper-backports/universe Packages
  403 Forbidden
Vrhe http://fi.archive.ubuntu.com dapper-updates/restricted Packages
  403 Forbidden
Vrhe http://archive.ubuntu.com dapper-backports/multiverse Packages
  403 Forbidden
Vrhe http://fi.archive.ubuntu.com dapper-updates/main Sources
  403 Forbidden
Vrhe http://archive.ubuntu.com dapper-backports/restricted Packages
  403 Forbidden
Vrhe http://fi.archive.ubuntu.com dapper-updates/restricted Sources
  403 Forbidden
Tiedoston http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-i386/Packages.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://dtw.silverentertainment.fi/oo2-soikko/dists/gcc34/non-free/binary-i386/Packages.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/source/Sources.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://fi.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/source/Sources.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://fi.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://fi.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://fi.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://fi.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://fi.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://fi.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz nouto ei onnistunut  403 Forbidden
Tiedoston http://fi.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz nouto ei onnistunut  403 Forbidden
Luetaan pakettiluetteloita... Valmis
E: Joidenkin hakemistotiedostojen nouto ei onnistunut, ne on ohitettu tai käytetty vanhoja.

```

---

### Post by aysiu on 2006-07-01
[Read this entire thread](http://www.ubuntuforums.org/showthread.php?t=186455) and see if something in there solves your problem.

---

### Post by Owdy on 2006-07-01
[quote=aysiu][Read this entire thread]("http://www.ubuntuforums.org/showthread.php?t=186455") and see if something in there solves your problem.[/quote] Nope.

---

### Post by aysiu on 2006-07-01
Shoot. I have no idea, then.

---

### Post by Owdy on 2006-07-02
[http://www.ubuntuforums.org/showpost.php?p=1205027&postcount=17](http://www.ubuntuforums.org/showpost.php?p=1205027&postcount=17)
solved

---

