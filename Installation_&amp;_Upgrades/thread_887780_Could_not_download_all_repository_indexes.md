---
title: "Could not download all repository indexes"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by wandman on 2008-08-12
I am fairly new to Linux. When trying to use the Update Manager I get the following Error message:

```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.1)]/dists/hardy/multiverse/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.1)]/dists/hardy/universe/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

```

Any ideas what I can do to rectify the situation?

---

### Post by oldos2er on 2008-08-12
Go into System, Administration, Software Sources, and uncheck the box next to CD-ROM.

---

### Post by wandman on 2008-08-12
Brilliant! That fixed it thank you.

---

### Post by mshervey on 2009-01-19
I too just installed Ubuntu for the first time and am having the same issue, however when I follow this path, Go into System, Administration, Software Sources, and uncheck the box next to CD-ROM, I do not see an option to select/de-select the CD-ROM. 

I looked in all the tabs and the tab labelled, Ubuntu Software, just has a grey box under, "Installable from CD-ROM/DVD", To install from a CD-ROM or DVD, insert the medium into the drive.  Nothing to check or uncheck.

Any help would be appreciated to over come this.

---

### Post by Partyboi2 on 2009-01-19
> **mshervey said:**
> I too just installed Ubuntu for the first time and am having the same issue, however when I follow this path, Go into System, Administration, Software Sources, and uncheck the box next to CD-ROM, I do not see an option to select/de-select the CD-ROM. 

I looked in all the tabs and the tab labelled, Ubuntu Software, just has a grey box under, "Installable from CD-ROM/DVD", To install from a CD-ROM or DVD, insert the medium into the drive.  Nothing to check or uncheck.

Any help would be appreciated to over come this.
Can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /etc/apt/sources.list
```

---

### Post by sundeepA1 on 2009-05-18
i got 

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse restricted universe main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates multiverse restricted universe main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse restricted universe main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed multiverse restricted universe main
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex
deb [http://apt.wicd.net](http://apt.wicd.net) feisty extras


within the terminal

---

### Post by Partyboi2 on 2009-05-18
> **sundeepA1 said:**
> i got 

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse restricted universe main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates multiverse restricted universe main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse restricted universe main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed multiverse restricted universe main
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex
deb [http://apt.wicd.net](http://apt.wicd.net) feisty extras


within the terminal
You are using Feisty which has reached its end of life, I would suggest upgrading to a later version of Ubuntu like hardy, Intrepid or Jaunty.

---

### Post by sundeepA1 on 2009-05-18
when Iam updating i get this 
[http://ppa.launchpad.net/fta/ubuntu/dists/hardy/partner/binary-i386/Packages.gz:](http://ppa.launchpad.net/fta/ubuntu/dists/hardy/partner/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty/restricted/source/Sources.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty-security/restricted/source/Sources.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty-security/restricted/source/Sources.gz:) 404 Not Found

after closing i got messege
[http://ppa.launchpad.net/fta/ubuntu/dists/hardy/partner/binary-i386/Packages.gz:](http://ppa.launchpad.net/fta/ubuntu/dists/hardy/partner/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty/restricted/source/Sources.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty-security/restricted/source/Sources.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty-security/restricted/source/Sources.gz:) 404 Not Found

to update with 7.10 i clicked on the upgrade
I got Could not find the release notes 
The server may be overloaded. 

why does this occur??

---

### Post by Partyboi2 on 2009-05-18
> **sundeepA1 said:**
> when Iam updating i get this 
[http://ppa.launchpad.net/fta/ubuntu/dists/hardy/partner/binary-i386/Packages.gz:](http://ppa.launchpad.net/fta/ubuntu/dists/hardy/partner/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty/restricted/source/Sources.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty-security/restricted/source/Sources.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty-security/restricted/source/Sources.gz:) 404 Not Found

after closing i got messege
[http://ppa.launchpad.net/fta/ubuntu/dists/hardy/partner/binary-i386/Packages.gz:](http://ppa.launchpad.net/fta/ubuntu/dists/hardy/partner/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty/restricted/source/Sources.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ftp.ucr.ac.cr/ubuntu/dists/feisty-security/restricted/source/Sources.gz:](http://ftp.ucr.ac.cr/ubuntu/dists/feisty-security/restricted/source/Sources.gz:) 404 Not Found

to update with 7.10 i clicked on the upgrade
I got Could not find the release notes 
The server may be overloaded. 

why does this occur??
Gutsy (7.10) has reached its end of life as well, the easier way would be to backup all your important stuff and do a clean install of a later release.
Or you could have a look at [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/EOLUpgrades") on a possible way to upgrade.

---

