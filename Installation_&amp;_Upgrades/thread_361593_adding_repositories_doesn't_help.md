---
title: "adding repositories doesn't help"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by Tectuktitlay on 2007-02-14
Hi!

I've tried adding all universe and multiverse repositories in an attempt to download the package "unrar". But it doesn't seem to make a difference at all. How do I enable the extra repositories?

I've got Dapper Drake and my /etc/apt/sources.list looks like:

```
## Major bug fix updates produced after the final release of the
## distribution.
# deb http://nl.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# deb-src http://nl.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://nl.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://nl.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://nl.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

#deb http://security.ubuntu.com/ubuntu dapper-security main restricted
#deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
```

I hope someone can give me some advice.
Thanks,

Maarten

---

### Post by taurus on 2007-02-14
Why don't you edit /etc/apt/sources.list and remove the # in front of all those deb lines.  Save it and then run

```
sudo aptitude update
sudo aptitude install unrar
```

---

### Post by Tectuktitlay on 2007-02-14
Hi Taurus,

Thanx for your attention!
I removed all comment hashes but I still get:

```

nusku:/# sudo aptitude install unrar
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for unrar
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

Just found out I can't get g++-package either...

Maarten

---

### Post by taurus on 2007-02-14
What happens when you run these commands?

```
sudo aptitude update
sudo aptitude install build-essential
```
G++ is part of the build-essential package.

---

### Post by Tectuktitlay on 2007-02-14
Tried it:

```

nusku:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://nl.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:2 http://nl.archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://nl.archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://nl.archive.ubuntu.com dapper-updates Release
Hit http://nl.archive.ubuntu.com dapper Release
Hit http://nl.archive.ubuntu.com dapper-backports Release
Hit http://nl.archive.ubuntu.com dapper-updates/main Packages
Hit http://nl.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://nl.archive.ubuntu.com dapper-updates/main Sources
Hit http://nl.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://nl.archive.ubuntu.com dapper/universe Packages
Hit http://nl.archive.ubuntu.com dapper/universe Sources
Hit http://nl.archive.ubuntu.com dapper-backports/main Packages
Hit http://nl.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://nl.archive.ubuntu.com dapper-backports/universe Packages
Hit http://nl.archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://nl.archive.ubuntu.com dapper-backports/main Sources
Hit http://nl.archive.ubuntu.com dapper-backports/restricted Sources
Hit http://nl.archive.ubuntu.com dapper-backports/universe Sources
Hit http://nl.archive.ubuntu.com dapper-backports/multiverse Sources
Get:4 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Fetched 4B in 1s (4B/s)
Reading package lists... Done
nusku:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for build-essential
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

No luck...

---

### Post by taurus on 2007-02-14
Remove the **nl.** from your repos in /etc/apt/sources.list and run those two commands again.

---

### Post by Tectuktitlay on 2007-02-14
Tried it, but again, no luck:

```

nusku:~$ sudo aptitude update

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Get:4 http://archive.ubuntu.com dapper-updates Release [50.9kB]
Get:5 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:6 http://archive.ubuntu.com dapper Release [34.8kB]
Get:7 http://archive.ubuntu.com dapper-backports Release [38.4kB]
Hit http://security.ubuntu.com dapper-security Release
Get:8 http://archive.ubuntu.com dapper-updates/main Packages [132kB]
Hit http://security.ubuntu.com dapper-security/main Packages
Get:9 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:10 http://archive.ubuntu.com dapper-updates/main Sources [48.4kB]
Get:11 http://archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get:12 http://archive.ubuntu.com dapper/universe Packages [2458kB]
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Get:13 http://archive.ubuntu.com dapper/universe Sources [975kB]
Get:14 http://archive.ubuntu.com dapper-backports/main Packages [13.0kB]
Get:15 http://archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:16 http://archive.ubuntu.com dapper-backports/universe Packages [44.9kB]
Get:17 http://archive.ubuntu.com dapper-backports/multiverse Packages [7071B]
Get:18 http://archive.ubuntu.com dapper-backports/main Sources [4308B]
Get:19 http://archive.ubuntu.com dapper-backports/restricted Sources [14B]
Get:20 http://archive.ubuntu.com dapper-backports/universe Sources [11.2kB]
Get:21 http://archive.ubuntu.com dapper-backports/multiverse Sources [2131B]
Fetched 3821kB in 10s (380kB/s)
Reading package lists... Done
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

nusku:~$ sudo apt-get update

Get:1 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper-backports Release
Get:4 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-backports/main Sources
Hit http://archive.ubuntu.com dapper-backports/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/universe Sources
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Fetched 4B in 6s (1B/s)
Reading package lists... Done

nusku:~$ sudo aptitude install unrar

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for unrar
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

nusku:~$ sudo aptitude install build-essential

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for build-essential
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

---

### Post by Tectuktitlay on 2007-02-18
Hi Taurus,

All my problems were suddenly solved when I added the live-cd to the repositories. If anyone can explain it, I'd be interested. Just thought you or anyone stumbling across this thread might like to know.

Greetz,

Maarten

---

