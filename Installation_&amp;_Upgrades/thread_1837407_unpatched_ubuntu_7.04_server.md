---
title: "unpatched ubuntu 7.04 server"
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by Dynotrick on 2011-09-01
I have a server that I set up back in 2007 that has never been able to access the repositories, or any external IP due to firewall restrictions.  I've finally gotten those restrictions removed and want to update my server with security patches, and possibly to to a dist upgrade to the current LTS version.  

When running apt-get update i get the following output:

```
x@server:~$ sudo apt-get update
Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security Release.gpg
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty Release.gpg
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com feisty-security Release
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates Release.gpg
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty Release
Ign http://security.ubuntu.com feisty-security/main Packages
Ign http://us.archive.ubuntu.com feisty-updates Release
Ign http://security.ubuntu.com feisty-security/restricted Packages
Ign http://security.ubuntu.com feisty-security/main Sources
Ign http://security.ubuntu.com feisty-security/restricted Sources
Ign http://security.ubuntu.com feisty-security/universe Packages
Ign http://security.ubuntu.com feisty-security/universe Sources
Ign http://security.ubuntu.com feisty-security/multiverse Packages
Ign http://us.archive.ubuntu.com feisty/main Packages
Ign http://us.archive.ubuntu.com feisty/restricted Packages
Ign http://us.archive.ubuntu.com feisty/main Sources
Ign http://us.archive.ubuntu.com feisty/restricted Sources
Ign http://us.archive.ubuntu.com feisty/universe Packages
Ign http://us.archive.ubuntu.com feisty/universe Sources
Ign http://us.archive.ubuntu.com feisty/multiverse Packages
Ign http://security.ubuntu.com feisty-security/multiverse Sources
Err http://security.ubuntu.com feisty-security/main Packages
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com feisty-security/restricted Packages
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com feisty-security/main Sources
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com feisty-security/restricted Sources
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com feisty-security/universe Packages
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com feisty-security/universe Sources
  404 Not Found [IP: 91.189.92.166 80]
Ign http://us.archive.ubuntu.com feisty/multiverse Sources
Ign http://us.archive.ubuntu.com feisty-updates/main Packages
Ign http://us.archive.ubuntu.com feisty-updates/restricted Packages
Ign http://us.archive.ubuntu.com feisty-updates/main Sources
Ign http://us.archive.ubuntu.com feisty-updates/restricted Sources
Err http://us.archive.ubuntu.com feisty/main Packages
  404 Not Found [IP: 91.189.92.170 80]
Err http://us.archive.ubuntu.com feisty/restricted Packages
  404 Not Found [IP: 91.189.92.170 80]
Err http://us.archive.ubuntu.com feisty/main Sources
  404 Not Found [IP: 91.189.92.170 80]
Err http://us.archive.ubuntu.com feisty/restricted Sources
  404 Not Found [IP: 91.189.92.170 80]
Err http://security.ubuntu.com feisty-security/multiverse Packages
  404 Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com feisty-security/multiverse Sources
  404 Not Found [IP: 91.189.92.166 80]
Err http://us.archive.ubuntu.com feisty/universe Packages
  404 Not Found [IP: 91.189.92.170 80]
Err http://us.archive.ubuntu.com feisty/universe Sources
  404 Not Found [IP: 91.189.92.170 80]
Err http://us.archive.ubuntu.com feisty/multiverse Packages
  404 Not Found [IP: 91.189.92.170 80]
Err http://us.archive.ubuntu.com feisty/multiverse Sources
  404 Not Found [IP: 91.189.92.170 80]
Err http://us.archive.ubuntu.com feisty-updates/main Packages
  404 Not Found [IP: 91.189.92.170 80]
Err http://us.archive.ubuntu.com feisty-updates/restricted Packages
  404 Not Found [IP: 91.189.92.170 80]
Err http://us.archive.ubuntu.com feisty-updates/main Sources
  404 Not Found [IP: 91.189.92.170 80]
Err http://us.archive.ubuntu.com feisty-updates/restricted Sources
  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.92.166 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz  404 Not Found [IP: 91.189.92.170 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
x@server:~$

```

Should I be concerned about all the 404 errors, and what should I do to resolve?

---

### Post by snowpine on 2011-09-01
1. To apply all 7.04 patches through Oct 2008 (the date 7.04 went "end of life") edit your software sources:

```
sudo nano /etc/apt/sources.list
```

Change all URLs to old-releases.ubuntu.com, for example change this:

```
deb http://us.archive.ubuntu.com feisty main
```

to this:

```
deb http://old-releases.ubuntu.com feisty main
```

Now you should be able to:

```
sudo apt-get update
sudo apt-get upgrade
```

or:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

2. Ubuntu release upgrades (7.04 to 7.10 for example) are a subject of debate on the forums. Many users will share success stories, but conversely, many will suggest a fresh reinstall of 10.04 (the current LTS). 

Should you decide to upgrade 7.04 to 7.10 to 8.04 to 10.04, you'll find this guide invaluable:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Good luck! :)

---

### Post by Dynotrick on 2011-09-01
Thanks!!  That is what I was thinking but wasn't sure if there were any special concerns since my version is so old. 

After making the changes to the sources file it was able to update.
However the following sources are still giving 404 errors.

```
deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

Where should I point these to?

For following the upgrade path to 10.04, I read through the guide you linked and I feel fairly comfortable going ahead with that once I have the applied the updates through EOL for my current version.  
This is a production server however and I don't have physical access to it should anything go wrong.  It is running LAMP and serving a single website.  Additional services running are SSH, ProFTPD, PHPmyadmin, and Webmin.  Do you think there are any major concerns with these while following the upgrade path?

---

### Post by Dynotrick on 2011-09-01
I think I found the answer, skipped right over it - duh...

Those should point to these right?

```
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted 
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security universe 
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security multiverse
```

---

