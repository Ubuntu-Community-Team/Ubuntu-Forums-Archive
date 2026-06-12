---
title: "Synaptic update errors..."
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by jcoyle on 2007-10-09
Hi,

Apologies if this has been answered elsewhere but i've searched and cant find anything.

Basically, Im fairly new to Ubuntu and my problem is this: 

When i click the orange update button on the menu bar at the top, it shows 32 updates available, but with a download size of None. I click install updates and it says installing updates, but then returns to Synaptic with 32 updates still showing and the update icon in the menu bar goes gray and says "a package manager is running". 

Could there be something wrong with my /etc/apt/sources.list file? I'll post it here anyway and the output from "sudo apt-get update".

I did have a GPG error with a backports server, but removed that from the third party software sources list and that error went away.

**_Contents of /etc/apt/sources.list**_

```
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
# deb http://www.backports.org/debian sarge-backports main
```


**_Output from sudo apt-get update:_**

```
Get: 1 http://gb.archive.ubuntu.com feisty Release.gpg [191B]
Hit http://gb.archive.ubuntu.com feisty/main Translation-en_GB
Get: 2 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com feisty/multiverse Translation-en_GB
Get: 3 http://gb.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://gb.archive.ubuntu.com feisty-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-updates/universe Translation-en_GB
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_GB
Ign http://security.ubuntu.com feisty-security/universe Translation-en_GB
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com feisty-security Release
Ign http://gb.archive.ubuntu.com feisty-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com feisty Release
Hit http://gb.archive.ubuntu.com feisty-updates Release
Hit http://security.ubuntu.com feisty-security/main Packages        
Hit http://gb.archive.ubuntu.com feisty/main Packages               
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://gb.archive.ubuntu.com feisty/restricted Packages
Hit http://gb.archive.ubuntu.com feisty/universe Packages
Hit http://gb.archive.ubuntu.com feisty/multiverse Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://gb.archive.ubuntu.com feisty/main Sources
Hit http://gb.archive.ubuntu.com feisty/restricted Sources
Hit http://gb.archive.ubuntu.com feisty/universe Sources
Hit http://gb.archive.ubuntu.com feisty/multiverse Sources
Hit http://gb.archive.ubuntu.com feisty-updates/main Packages
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://gb.archive.ubuntu.com feisty-updates/universe Packages
Hit http://gb.archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com feisty-updates/main Sources
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://gb.archive.ubuntu.com feisty-updates/universe Sources
Hit http://gb.archive.ubuntu.com feisty-updates/multiverse Sources
Fetched 3B in 0s (4B/s)  
Reading package lists... Done
```


Any help would be greatly appreciated.


Joe.


p.s. apologies for the length of the post - wanted to provide as much information as possible.

---

### Post by bapoumba on 2007-10-09
Please run:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Your source.list is fine, and so is the update output.

---

### Post by jcoyle on 2007-10-09
Hi, thanks for the quick response. The apt-get update command worked fine however the apt-get dist-upgrade produced an error right at the end. See the output below:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  app-install-data-commercial fetchmail libmagick9 libsndfile1 libssl0.9.8
  linux-headers-2.6.20-16 linux-headers-2.6.20-16-generic
  linux-image-2.6.20-16-generic linux-libc-dev openoffice.org
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-java-common openoffice.org-math
  openoffice.org-style-andromeda openoffice.org-style-default
  openoffice.org-style-human openoffice.org-style-industrial
  openoffice.org-writer openssl python-uno ttf-opensymbol update-manager
  update-manager-core
32 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/120MB of archives.
After unpacking 8192B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Extract templates from packages: 100%
Preconfiguring packages ...
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Thanks again for the response.
Any other ideas appreciated.


Joe.

---

### Post by taurus on 2007-10-09
What's the output of this command from a terminal?

```
ls -la /var/lib/dpkg/available
```

---

### Post by jcoyle on 2007-10-10
The output of "ls -la /var/lib/dpkg/available" was the following:

```
ls: /var/lib/dpkg/available: No such file or directory
```


Thanks.

Joe.

---

### Post by jcoyle on 2007-10-11
Hey guys,

I have just posted a screen shot of the update manager when its displayed download size:none.

Can you make heads or tails of it?

Is there a way to clean out a cache of these updates and start again?


Thanks

Joe.

---

### Post by jcoyle on 2007-10-11
I've fixed it - i had to run the following code:

```

sudo dpkg --clear-avail
sudo apt-get update

```


Dont know what caused the problem, but nevermind!

Thanks again

Joe.

---

