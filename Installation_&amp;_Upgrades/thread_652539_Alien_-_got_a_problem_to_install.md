---
title: "Alien - got a problem to install"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by ntxploits on 2007-12-28
i try to follow the manual from this site...

[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)

```
$sudo apt-get update
```

however, a few of errors appear

> Ign [http://blueeyedcreature.net](http://blueeyedcreature.net) ./ Packages
Hit [http://blueeyedcreature.net](http://blueeyedcreature.net) ./ Packages
Fetched 21.9kB in 14s (1476B/s)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/dapper/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/dapper/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/dapper/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/dapper/free/source/Sources.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/dapper/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/dapper/non-free/source/Sources.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


```
ntxploits@ntxploits-desktop:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  alien: Depends: debhelper (>= 3) but it is not going to be installed
  dpkg: Breaks: dpkg-dev (< 1.14.0) but 1.13.11ubuntu7 is to be installed
E: Broken packages

```

what should i do to rectify this problem. thanks

---

### Post by rsambuca on 2007-12-28
> **ntxploits said:**
> i try to follow the manual from this site...

[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)

```
$sudo apt-get update
```

however, a few of errors apper



```
ntxploits@ntxploits-desktop:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  alien: Depends: debhelper (>= 3) but it is not going to be installed
  dpkg: Breaks: dpkg-dev (< 1.14.0) but 1.13.11ubuntu7 is to be installed
E: Broken packages

```

what should i do to rectify this problem. thanks

Are you running Dapper (6.06)?

---

### Post by ntxploits on 2007-12-28
thanks for your reply

i'm new to this...because i'm sure what to do, google for info and found this

[http://www.debianadmin.com/find-your-debian-or-ubuntu-linux-version-you-are-running.html](http://www.debianadmin.com/find-your-debian-or-ubuntu-linux-version-you-are-running.html)

```
cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"
```
```

Linux ntxploits-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
```

---

### Post by rsambuca on 2007-12-28
> **ntxploits said:**
> thanks for your reply

i'm new to this...because i'm sure what to do, google for info and found this

[http://www.debianadmin.com/find-your-debian-or-ubuntu-linux-version-you-are-running.html](http://www.debianadmin.com/find-your-debian-or-ubuntu-linux-version-you-are-running.html)

```
cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"
```
```

Linux ntxploits-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
```

I am afraid you have a messed up sources list.  You are running gutsy, but you have somehow added repositories for older versions of Ubuntu.  Eventually this could cause quite a bit of havoc.  If you post the output of the following, we should be able to get things straightened out.```
cat /etc/apt/sources.list
```

---

### Post by ntxploits on 2007-12-28
thanks..here is the file
actually, i just modified the original file based on this article

[http://www.groupsrv.com/linux/about109039.html](http://www.groupsrv.com/linux/about109039.html)

```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in
# this file and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb-src http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb-src http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

# Upstream Wine
deb http://wine.budgetdedicated.com/apt dapper main

deb-src http://wine.budgetdedicated.com/apt dapper main

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ dapper free non-free

deb-src http://medibuntu.sos-sts.com/repo/ dapper free non-free

# Canonical Commercial packages
# GPG key: 437D05B5
deb http://archive.canonical.com dapper-commercial main

deb-src http://archive.canonical.com dapper-commercial main

#ubuntu-lite Packages

deb http://blueeyedcreature.net/ubuntu ./

#swiftfox

deb http://getswiftfox.com/builds/debian unstable non-free



deb http://www.getautomatix.com/apt dapper main


#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END

```

---

### Post by Partyboi2 on 2007-12-28
You will need to change back to a Gusty source.list to fix and prevent more problems in the future. You will need to generate a new source.list but make sure you choose "Gusty"
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
Open up your source.list
```
Press Alt+F2
```type
```
gksudo gedit /etc/apt/sources.list
```when the source.list open, delete the contents and copy and paste the new one from source-o-matic.
then save it.
Once you have replaced it
run in a terminal
```
sudo apt-get update
``````
sudo apt-get install alien
```

---

