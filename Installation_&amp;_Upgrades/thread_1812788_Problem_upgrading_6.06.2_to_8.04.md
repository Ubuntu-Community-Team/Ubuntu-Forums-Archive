---
title: "Problem upgrading 6.06.2 to 8.04"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by MorningSleeper on 2011-07-26
I noticed Dapper 6.06 LTS recently reached EOL and am trying to remotely upgrade server version of Dapper 6.06.2 LTS to Hardy 8.04 LTS which is not yet EOL. Dapper is up to date. According to the following page:
 
[https://help.ubuntu.com/community/EOLUpgrades/Dapper](https://help.ubuntu.com/community/EOLUpgrades/Dapper)
 
/etc/apt/sources.list should have
 
 
```
## EOL upgrade sources.list
# Required
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
 
# Optional
#deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
```
 
when I put those in the file and run sudo do-release-upgrade I get the following:
 
```

 
root@server1:/home/admin# sudo do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'hardy.tar.gz'
authenticate 'hardy.tar.gz' against 'hardy.tar.gz.gpg'
Reading cache
Checking package manager
Reading package lists: Done
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done
WARNING: Failed to read mirror file
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Done downloading
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Done downloading
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Done downloading
Reading package lists: Done
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done
WARNING: Failed to read mirror file
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports Release.gpg
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports Release
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports/main/debian-installer Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports/main/debian-installer Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Done downloading
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports Release.gpg
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports Release
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports/main/debian-installer Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Done downloading
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports Release.gpg
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports Release
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports/main/debian-installer Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) dapper-backports/main/debian-installer Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Done downloading
Reading package lists: Done
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done
Getting upgrade prerequisites failed
The system was unable to get the prerequisites for the upgrade. The
upgrade will abort now and restore the original system state.
Please report this as a bug against the 'update-manager' package and
include the files in /var/log/dist-upgrade/ in the bugreport.
 
Restoring original system state
Aborting
Reading package lists: Done
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done
root@server1:/home/admin#

```
 
The log file shows:
 
```
2011-07-26 16:34:24,330 INFO release-upgrader version '0.87.31' started
2011-07-26 16:34:24,334 DEBUG Using 'DistUpgradeViewText' view
2011-07-26 16:34:24,393 DEBUG enable dpkg --force-overwrite
2011-07-26 16:34:24,451 DEBUG lsb-release: 'dapper'
2011-07-26 16:34:24,451 DEBUG _pythonSymlinkCheck run
2011-07-26 16:34:24,604 DEBUG checkViewDepends()
2011-07-26 16:34:24,605 DEBUG need backports
2011-07-26 16:34:24,605 DEBUG getRequiredBackports()
2011-07-26 16:34:24,605 DEBUG writing prereuists sources.list at: '/etc/apt/sources.list.d/prerequists-sources.dapper.list' 
2011-07-26 16:34:24,643 DEBUG adding '# sources.list fragment for pre-requists (mirror from sources.list + fallback)
' prerequists
2011-07-26 16:34:24,643 DEBUG adding '# this is safe to remove after the upgrade
' prerequists
2011-07-26 16:34:24,643 DEBUG adding '
' prerequists
2011-07-26 16:34:24,644 DEBUG adding 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main/debian-installer
' prerequists
2011-07-26 16:34:24,644 DEBUG running doUpdate() (showErrors=False)
2011-07-26 16:34:26,380 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
'. Retrying (currentRetry: 0)
2011-07-26 16:34:28,246 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.170 80]
'. Retrying (currentRetry: 1)
2011-07-26 16:34:29,949 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
'. Retrying (currentRetry: 2)
2011-07-26 16:34:29,950 ERROR doUpdate() failed completely
2011-07-26 16:34:29,992 ERROR Can not find backport 'release-upgrader-apt'
2011-07-26 16:34:29,993 DEBUG writing prereuists sources.list at: '/etc/apt/sources.list.d/prerequists-sources.dapper.list' 
2011-07-26 16:34:30,025 DEBUG adding '# sources.list fragment for pre-requists (mirror from sources.list + fallback)
' prerequists
2011-07-26 16:34:30,025 DEBUG adding '# this is safe to remove after the upgrade
' prerequists
2011-07-26 16:34:30,025 DEBUG adding 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main/debian-installer
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main/debian-installer
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-backports main/debian-installer
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main/debian-installer
' prerequists
2011-07-26 16:34:30,025 DEBUG adding 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main/debian-installer
' prerequists
2011-07-26 16:34:30,025 DEBUG running doUpdate() (showErrors=False)
2011-07-26 16:34:32,061 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.40 80]
'. Retrying (currentRetry: 0)
2011-07-26 16:34:33,915 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
'. Retrying (currentRetry: 1)
2011-07-26 16:34:35,954 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
'. Retrying (currentRetry: 2)
2011-07-26 16:34:35,955 ERROR doUpdate() failed completely
2011-07-26 16:34:35,994 ERROR Can not find backport 'release-upgrader-apt'
2011-07-26 16:34:35,994 WARNING no backport for 'release-upgrader-apt' found

```
 
It looks like the URLs have been removed from the server. Don't know if this is by mistake or design when a version reaches EOL. Anyway, I found on the following page:
 
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
 
it mentioned to use a different set of URLs in sources.list and the sub domains seem to suggest they are the place for EOL versions:
 
```
## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
 
# Optional
#deb http://old-releases.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
```
 
So I edited sources.list again and tried sudo do-release-upgrade and get the following:
 
```
root@server1:/home/admin# sudo do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'hardy.tar.gz'
authenticate 'hardy.tar.gz' against 'hardy.tar.gz.gpg'
Reading cache
Checking package manager
Reading package lists: Done
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done
WARNING: Failed to read mirror file
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/main Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/restricted Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/main Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/restricted Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/universe Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/multiverse Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/universe Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/multiverse Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/main Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/restricted Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/main Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/restricted Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/universe Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/multiverse Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/universe Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/multiverse Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/main Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/restricted Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/main Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/restricted Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/universe Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/multiverse Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/universe Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/multiverse Packages
Done downloading
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/multiverse Packages
Done downloading
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/multiverse Packages
Done downloading
Reading package lists: Donecom dapper-security/multiverse Packages: 97
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done
WARNING: Failed to read mirror file
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/multiverse Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/multiverse Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
100% [Working]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)
It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.
You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.
Failed [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Done downloading
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Invalid argument
        Input file = (stdin), output file = (stdout)
It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.
You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Done downloading
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Done downloading
Reading package lists: Donecom dapper-backports/main/debian-installer Packages: 97
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done
Getting upgrade prerequisites failed
The system was unable to get the prerequisites for the upgrade. The
upgrade will abort now and restore the original system state.
Please report this as a bug against the 'update-manager' package and
include the files in /var/log/dist-upgrade/ in the bugreport.
 
Restoring original system state
Aborting
Reading package lists: Done
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done
root@server1:/home/admin#

```
 
The log file shows:
 
```
2011-07-26 16:39:49,437 INFO release-upgrader version '0.87.31' started
2011-07-26 16:39:49,441 DEBUG Using 'DistUpgradeViewText' view
2011-07-26 16:39:49,498 DEBUG enable dpkg --force-overwrite
2011-07-26 16:39:49,557 DEBUG lsb-release: 'dapper'
2011-07-26 16:39:49,557 DEBUG _pythonSymlinkCheck run
2011-07-26 16:39:49,648 DEBUG checkViewDepends()
2011-07-26 16:39:49,649 DEBUG need backports
2011-07-26 16:39:49,649 DEBUG getRequiredBackports()
2011-07-26 16:39:49,649 DEBUG writing prereuists sources.list at: '/etc/apt/sources.list.d/prerequists-sources.dapper.list' 
2011-07-26 16:39:49,690 DEBUG adding '# sources.list fragment for pre-requists (mirror from sources.list + fallback)
' prerequists
2011-07-26 16:39:49,690 DEBUG adding '# this is safe to remove after the upgrade
' prerequists
2011-07-26 16:39:49,691 DEBUG adding '
' prerequists
2011-07-26 16:39:49,691 DEBUG adding 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main/debian-installer
' prerequists
2011-07-26 16:39:49,691 DEBUG running doUpdate() (showErrors=False)
2011-07-26 16:40:01,363 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
'. Retrying (currentRetry: 0)
2011-07-26 16:40:02,612 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
'. Retrying (currentRetry: 1)
2011-07-26 16:40:03,865 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.170 80]
'. Retrying (currentRetry: 2)
2011-07-26 16:40:03,865 ERROR doUpdate() failed completely
2011-07-26 16:40:10,769 ERROR Can not find backport 'release-upgrader-apt'
2011-07-26 16:40:10,770 DEBUG writing prereuists sources.list at: '/etc/apt/sources.list.d/prerequists-sources.dapper.list' 
2011-07-26 16:40:10,808 DEBUG adding '# sources.list fragment for pre-requists (mirror from sources.list + fallback)
' prerequists
2011-07-26 16:40:10,808 DEBUG adding '# this is safe to remove after the upgrade
' prerequists
2011-07-26 16:40:10,809 DEBUG adding 'deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) dapper-backports main/debian-installer
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) dapper-backports main/debian-installer
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) dapper-backports main/debian-installer
' prerequists
2011-07-26 16:40:10,809 DEBUG adding 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main/debian-installer
' prerequists
2011-07-26 16:40:10,809 DEBUG running doUpdate() (showErrors=False)
2011-07-26 16:40:12,437 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.bz2](http://old-releases.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.bz2) Could not open file /var/lib/apt/lists/partial/old-releases.ubuntu.com_ubuntu_dists_dapper-backports_main_debian-installer_binary-i386_Packages - open (2 No such file or directory)
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.bz2](http://old-releases.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.bz2) Could not open file /var/lib/apt/lists/partial/old-releases.ubuntu.com_ubuntu_dists_dapper-backports_main_debian-installer_binary-i386_Packages - open (2 No such file or directory)
'. Retrying (currentRetry: 0)
2011-07-26 16:40:13,863 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
'. Retrying (currentRetry: 1)
2011-07-26 16:40:15,276 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
'. Retrying (currentRetry: 2)
2011-07-26 16:40:15,276 ERROR doUpdate() failed completely

```
 
While a lot less 404 errors, it looks like it is still trying to fetch a file at [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) that is returning a 404 error even though I removed all lines containing archive.ubuntu.com from sources.list. From the log it looks like the upgrade process is adding that URL to '/etc/apt/sources.list.d/prerequists-sources.dapper.list'. Since the line is related to backports I tried uncommenting the optional line in sources.list related to backports:
 
```

## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
# Optional
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

```
 
ran sudo do-release-upgrade again
 
```

root@server1:/home/admin# sudo do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'hardy.tar.gz'
authenticate 'hardy.tar.gz' against 'hardy.tar.gz.gpg'
Reading cache
Checking package manager
Reading package lists: Done
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done
WARNING: Failed to read mirror file
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/multiverse Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/restricted Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/restricted Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/universe Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/multiverse Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/universe Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/multiverse Packages
Done downloading
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/multiverse Packages
Done downloading
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/restricted Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/multiverse Packages
Done downloading
Reading package lists: Donecom dapper-backports/multiverse Packages: 97
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done
WARNING: Failed to read mirror file
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Done downloading
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/restricted Packages
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Done downloading
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release.gpg
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security Release
Ignored [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Done [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports Release
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-security/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/restricted Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) dapper-backports/main/debian-installer Packages
Done downloading
Reading package lists: Donecom dapper-backports/main/debian-installer Packages: 97
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done
Getting upgrade prerequisites failed
The system was unable to get the prerequisites for the upgrade. The
upgrade will abort now and restore the original system state.
Please report this as a bug against the 'update-manager' package and
include the files in /var/log/dist-upgrade/ in the bugreport.
 
Restoring original system state
Aborting
Reading package lists: Done
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done
root@server1:/home/admin#

```
 
and the log file ...
 
```

2011-07-26 18:23:36,519 INFO release-upgrader version '0.87.31' started
2011-07-26 18:23:36,523 DEBUG Using 'DistUpgradeViewText' view
2011-07-26 18:23:36,584 DEBUG enable dpkg --force-overwrite
2011-07-26 18:23:36,645 DEBUG lsb-release: 'dapper'
2011-07-26 18:23:36,645 DEBUG _pythonSymlinkCheck run
2011-07-26 18:23:37,139 DEBUG checkViewDepends()
2011-07-26 18:23:37,139 DEBUG need backports
2011-07-26 18:23:37,139 DEBUG getRequiredBackports()
2011-07-26 18:23:37,139 DEBUG writing prereuists sources.list at: '/etc/apt/sources.list.d/prerequists-sources.dapper.list' 
2011-07-26 18:23:37,185 DEBUG adding '# sources.list fragment for pre-requists (mirror from sources.list + fallback)
' prerequists
2011-07-26 18:23:37,185 DEBUG adding '# this is safe to remove after the upgrade
' prerequists
2011-07-26 18:23:37,185 DEBUG adding '
' prerequists
2011-07-26 18:23:37,186 DEBUG adding 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main/debian-installer
' prerequists
2011-07-26 18:23:37,186 DEBUG running doUpdate() (showErrors=False)
2011-07-26 18:23:39,177 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
'. Retrying (currentRetry: 0)
2011-07-26 18:23:40,572 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.170 80]
'. Retrying (currentRetry: 1)
2011-07-26 18:23:41,818 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.171 80]
'. Retrying (currentRetry: 2)
2011-07-26 18:23:41,819 ERROR doUpdate() failed completely
2011-07-26 18:23:43,621 ERROR Can not find backport 'release-upgrader-apt'
2011-07-26 18:23:43,622 DEBUG writing prereuists sources.list at: '/etc/apt/sources.list.d/prerequists-sources.dapper.list' 
2011-07-26 18:23:43,663 DEBUG adding '# sources.list fragment for pre-requists (mirror from sources.list + fallback)
' prerequists
2011-07-26 18:23:43,663 DEBUG adding '# this is safe to remove after the upgrade
' prerequists
2011-07-26 18:23:43,663 DEBUG adding 'deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) dapper-backports main/debian-installer
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) dapper-backports main/debian-installer
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) dapper-backports main/debian-installer
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) dapper-backports main/debian-installer
' prerequists
2011-07-26 18:23:43,664 DEBUG adding 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main/debian-installer
' prerequists
2011-07-26 18:23:43,664 DEBUG running doUpdate() (showErrors=False)
2011-07-26 18:23:45,061 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]
'. Retrying (currentRetry: 0)
2011-07-26 18:23:46,462 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
'. Retrying (currentRetry: 1)
2011-07-26 18:23:47,866 ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.169 80]
'. Retrying (currentRetry: 2)
2011-07-26 18:23:47,866 ERROR doUpdate() failed completely

```
 
but the upgrade process is still inserting the same 404 file location into '/etc/apt/sources.list.d/prerequists-sources.dapper.list'. I tried to edit the dapper section in /var/lib/update-manager/meta-release-lts from:
 
```

Dist: dapper
Name: Dapper Drake
Version: 6.06 LTS
Date: Thu, 01 Jun 2006 9:00:00 UTC
Supported: 0
Description: This is the Dapper Drake release
Release-File: [http://[COLOR=#0066cc]archive[/COLOR].ubuntu.com/ubuntu/dists/dapper/Release]("http://archieve.ubuntu.com/ubuntu/dists/dapper/Release")
ReleaseNotes: [http://changelogs.ubuntu.com/EOLReleaseAnnouncement](http://changelogs.ubuntu.com/EOLReleaseAnnouncement)
UpgradeTool: [http://archive.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz)
UpgradeToolSignature: [http://archive.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz.gpg)
Dist: hardy 
Name: Hardy Heron
Version: 8.04.1 LTS
Date: Thu, 24 Apr 2008 12:00:00 UTC
Supported: 1
Description: This is the 8.04.1 LTS release
Release-File: [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)
ReleaseNotes: [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.31/ReleaseAnnouncement](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.31/ReleaseAnnouncement)
UpgradeTool: [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.31/hardy.tar.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.31/hardy.tar.gz)
UpgradeToolSignature: [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.31/hardy.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.31/hardy.tar.gz.gpg)
Dist: lucid
Name: Lucid Lynx
Version: 10.04.3 LTS
Date: Thu, 29 Apr 2010 12:00:00 UTC
Supported: 1
Description: This is the 10.04.3 LTS release
Release-File: [http://archive.ubuntu.com/ubuntu/dists/lucid/Release](http://archive.ubuntu.com/ubuntu/dists/lucid/Release)
ReleaseNotes: [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/ReleaseAnnouncement](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/ReleaseAnnouncement)
ReleaseNotesHtml: [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/ReleaseAnnouncement](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/ReleaseAnnouncement)
UpgradeTool: [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/lucid.tar.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/lucid.tar.gz)
UpgradeToolSignature: [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/lucid.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/lucid.tar.gz.gpg)

```
 
to
 
```

Dist: dapper
Name: Dapper Drake
Version: 6.06 LTS
Date: Thu, 01 Jun 2006 9:00:00 UTC
Supported: 0
Description: This is the Dapper Drake release
Release-File: [http://old-releases.ubuntu.com/ubuntu/dists/dapper/Release](http://old-releases.ubuntu.com/ubuntu/dists/dapper/Release)
ReleaseNotes: [http://changelogs.ubuntu.com/EOLReleaseAnnouncement](http://changelogs.ubuntu.com/EOLReleaseAnnouncement)
UpgradeTool: [http://old-releases.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz](http://old-releases.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz)
UpgradeToolSignature: [http://old-releases.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz.gpg](http://old-releases.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz.gpg)
Dist: hardy 
Name: Hardy Heron
Version: 8.04.1 LTS
Date: Thu, 24 Apr 2008 12:00:00 UTC
Supported: 1
Description: This is the 8.04.1 LTS release
Release-File: [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)
ReleaseNotes: [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.31/ReleaseAnnouncement](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.31/ReleaseAnnouncement)
UpgradeTool: [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.31/hardy.tar.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.31/hardy.tar.gz)
UpgradeToolSignature: [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.31/hardy.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.31/hardy.tar.gz.gpg)
Dist: lucid
Name: Lucid Lynx
Version: 10.04.3 LTS
Date: Thu, 29 Apr 2010 12:00:00 UTC
Supported: 1
Description: This is the 10.04.3 LTS release
Release-File: [http://archive.ubuntu.com/ubuntu/dists/lucid/Release](http://archive.ubuntu.com/ubuntu/dists/lucid/Release)
ReleaseNotes: [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/ReleaseAnnouncement](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/ReleaseAnnouncement)
ReleaseNotesHtml: [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/ReleaseAnnouncement](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/ReleaseAnnouncement)
UpgradeTool: [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/lucid.tar.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/lucid.tar.gz)
UpgradeToolSignature: [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/lucid.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/dist-upgrader-all/current/lucid.tar.gz.gpg)

```
 
thinking it was getting the 404 from there but it had no effect. Then I noticed in:
 
/usr/lib/python2.4/site-packages/UpdateManager/MetaRelease.py
/usr/lib/python2.4/site-packages/UpdateManagerCore/MetaRelease.py
 
there was a reference to a page at ubuntu.com that contained archive.ubuntu.com and changed it from a URI at their site:
 
METARELEASE_URI = "[http://changelogs.ubuntu.com/meta-release-lts](http://changelogs.ubuntu.com/meta-release-lts)"
 
to a URI at my own site with the file edited to reflect the old-releases.ubuntu.com instead of archives.ubuntu.com but still no effect.
 
Anyone have any ideas what is inserting that 404 URL to that archive sub domain or what else I could try?

---

### Post by MorningSleeper on 2011-07-27
While not dapper to hardy, the following bug report details a similar problem and it looks like it might be caused from a file in the 'hardy.tar.gz' that is extracted called DistUpgradeControler.py during the upgrade process. Looks like the file may rewrite the /etc/apt/sources.list and/or 
/etc/apt/sources.list.d/prerequists-sources.list file with the archive sub domain instead of the old-releases sub domain during the upgrade causing the 404 server error since it is no longer there.
 
[https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/264181](https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/264181)
 
The end of the first post offers a work around but I have not tried it. Basically looks like you go edit the sources.list after the upgrade process fails and then try to restart the upgrade process from where it left off. Another more complicated work around to the same issue is offered in the last three posts of the following bug report but it too I have not tried.
 
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/62184](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/62184)
 
If anyone is able to get theirs upgraded using either of the above or other methods, please let me know.

---

