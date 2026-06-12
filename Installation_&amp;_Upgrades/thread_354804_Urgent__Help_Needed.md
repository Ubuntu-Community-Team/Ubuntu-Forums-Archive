---
title: "Urgent ???? Help Needed"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by ambuj123 on 2007-02-06
Hello
well i am running ubuntu 6.06 now i got this ubuntu 6.10 cd today now i wanted to upgrade ubuntu from within the ubuntu os not a fresh installation. now i did not knew that it was possible but after placing cd in the drive while running ubuntu it showed it can be upgraded to ubuntu 6.10 without fresh install , however it started downloading stuff from the internet instead of using the repositories on the cd since here we are charged per mb download from internet  so i cancelled the process.  now when i start installation after removing all the online repositories and adding only the ubuntu 6.10 repositorie in software properties  it shows that all packages are already updated but i am sure it is not since the cd was not more than 3 minutes in the drive when i cancelled update process. even running the cdromupgrade shell script in cd shows there are no package to update so basically i feel packages have not been updated but it has been stored somewhere that packages are updated how can i correct it plz? help

---

### Post by Jussi Kukkonen on 2007-02-06
please paste the contents of */etc/apt/sources.list* here.

Also, you might want to change the title of your post to something meaningful -- using a generic title like "Urgent! Help!" implies you aren't willing to spend the minute it takes to come up with a good title... I'm sure you don't want that.

---

### Post by ambuj123 on 2007-02-06
> ## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free
# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted




here is the content .

and i would try to refrain from using such title for the posts .:)

---

### Post by Jussi Kukkonen on 2007-02-06
[updated instructions...]
First, yous should make sure you have ubuntu-desktop -package installed. I you don't, you should revert your sources.list to what it was with dapper, and run  ***sudo apt-get install ubuntu-desktop***

Then the upgrade:
To upgrade cleanly you need to have the cdrom line and the on-line repositories enabled, otherwise some programs may be uninstalled... Put the cdrom-line first, that means it will be tried first. This should work (use  ***gksudo gedit /etc/apt/sources.list*** to edit):
```
deb cdrom:/ edgy main restricted

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

## UPDATES
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
# deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb http://archive.canonical.com/ubuntu edgy-commercial main



## OLD, FIX TO EDGY BEFORE ENABLING
## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
# deb http://medibuntu.sos-sts.com/repo/ dapper free non-free
# deb-src http://medibuntu.sos-sts.com/repo/ dapper free non-free

```

Then run this to upgrade:
```
 sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade 
```

---

