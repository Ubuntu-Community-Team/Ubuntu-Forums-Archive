---
title: "Can't install Microsoft fonts"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by calande on 2006-06-24
I have tried just about everything to install the Microsoft fonts ](*,) 

I can't install the MS fonts. I tried Adept, I typed "Microsoft", I also typed "fonts", and the Microsoft didn't appear in the list. I also tried sudo apt-get install msttcorefonts, nothing:

```
charles@kubuntu:~$ sudo apt-get install msttcorefonts
Password:
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate
charles@kubuntu:~$
```

Here's my sources.list file with the multiverse servers enabled:

```

# Line commented out by installer because it failed to verify:
deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted 
# Line commented out by installer because it failed to verify:
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted 
# Line commented out by installer because it failed to verify:
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper universe 
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu dapper-security main 
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu dapper-security main 
deb http://security.ubuntu.com/ubuntu dapper-security universe 
deb-src http://security.ubuntu.com/ubuntu dapper-security universe 
deb http://deb.opera.com/opera/ stable non-free 
```

Also I did a sudo apt-get update several times before running the above. Seriously, something needs to be done to make sofware installation easier. Things don't work as expected. I installed Opera, and it's complaining about a number of things missing during startup (I followed [this tutorial]("https://wiki.ubuntu.com/OperaBrowser"), and did a sudo apt-get -f install, which didn't fix anything ](*,)

Neither Adept nor the terminal have had success so far. Anyway, if you could help me for the Microsoft fonts, that would be cool. Is there a wishlist at Ubuntu so that I ask for something easier to install software? It should be like on Windows or OS X, it always works at least :neutral:

---

### Post by Winblowz on 2006-06-24
I don't think you have the multiverse repository enabled. To make it easy, replace your /etc/apt/sources.list with the following (copy and paste)...
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free 
```

---

### Post by rcarring on 2006-06-24
Change your repos to point to uk in place of au.

These are really fast and work, the us ones occasionally dawdle, cough and fall over.

---

### Post by calande on 2006-06-26
Winblowz: Thank you, this worked fine. Any idea how to add the Opera link to my K Menu?

rcarring: Thanks buddy, I think I saw you on another forum, didn't I? :)

---

### Post by thebigfatgeek on 2006-07-02
I chnaged the source list but unfortunately on reloading of the package database it fails on packages.freecontrib.org. Any other ideas on how to trace the cause of the problem?

---

### Post by rcarring on 2006-07-02
@thebigfatgeek

I guess you could comment out the packages.freecontrib.org line just so as to get the rest of the software installed and configured.

If you have a friend that has a Windows computer, you could stick the fonts on a floppy or in a zip and email them to yourself, then extract them to a temp folder before copying and pasting them into the fonts folder.

If you use nautilus then Ctrl-L and type in fonts:/// to open the folder.

----

@calande

I am also active from time to time on pc-bsd and open office and some windows related forums. I recognize the avatar =D

---

