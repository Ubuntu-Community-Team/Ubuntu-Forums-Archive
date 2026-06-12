---
title: "Updates with old breezy release and upgrading"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by antimatter on 2007-12-13
Hi! Im using an old Laptop to get online at the moment and its running the old 5.10 breezy badger release. 
I havent turned it on for about 1.5 years,but was forced to because my desktop broke. Anyway, the problem i have now is that i would like to update and install some programs but cant do so because apt-get is throwin 404s at me. do the old breezy depositories not exist anymore or did the urls change? i will paste my sources list:

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

#backup Mirror - FAST
#deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-backports main universe multiverse restricted
#deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-extras main universe multiverse restricted

#backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse


am i forced to move on the latest release now or is there any way i could get my hands on the old repositories? if i had to upgrade, would it be possible to upgrade directly to the latest release from 5.10? i would just download the latest iso and throw that into the drive right?


thanks for your assistance!

---

### Post by PmDematagoda on 2007-12-13
Breezy is not only very old, but support(And updates) has been finished for it a very long time back. Also you may run the risk of breaking the Ubuntu OS if you take the whole way up to Ubuntu 7.10 since you will need to upgrade to the next adjacent release and so on until you reach Ubuntu 7.10, this means a huge shift which could become a factor in breaking Ubuntu.

I would say that you would be better off doing a clean install of Ubuntu 7.10.

---

### Post by lonniehenry on 2007-12-13
I would suggest trying to burn an iso for Gutsy and run it live.  If you can run it live, then install it.  It may take some work but you should be able to do that.  There have been many advances and improvements in Ubuntu since Breezy days.  Early versions are no longer supported - that is why repos  are not there.

---

### Post by bapoumba on 2007-12-15
The repos for Ubuntu obsolete versions are here:
[http://old-releases.ubuntu.com/releases/]("http://old-releases.ubuntu.com/releases/")

Change archive.ubuntu.com in your sources.list to old-releases.ubuntu.com.

And as already said, you cannot safely upgrade from breezy to gusty.

---

