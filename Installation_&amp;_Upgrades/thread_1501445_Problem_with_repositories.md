---
title: "Problem with repositories"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by Nunners on 2010-06-04
I'm having a problem installing various things on a fresh install of 10.04 Lucid Server using apt-get.

I've updated the sources.list file to be:
```
deb http://archive.ubuntu.com/ubuntu lucid universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

#deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/ lucid main restricted

```

If I try installing say lshw (which wasn't installed for some reason) or webmin, nagios etc etc

```
sudo apt-get install <package_name>
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package webmin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package <package_name> has no installation candidate

```

I'm guessing I might have the wrong repos, but I'm not sure?

Thanks
Nunners

---

### Post by oldos2er on 2010-06-04
Looks like you're missing "main". Try [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by Nunners on 2010-06-08
Thanks - solved that a treat... only problem is now having apt-get problems....

---

