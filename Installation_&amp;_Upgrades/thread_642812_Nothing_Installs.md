---
title: "Nothing Installs"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by Sugi on 2007-12-17
I tryed to install wine, opera, and java.  Nothing installs.
What's wrong?  Why will nothing install?

Opera
libqt3-mt

java
> @GUTSY:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate


wine
> @GUTSY:~$ sudo apt-get update
[sudo] password for :
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Fetched 1B in 1s (1B/s)
Reading package lists... Done
midori@midoriGUTSY:~$ sudo apt-get install wine
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
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable
E: Broken packages


---

### Post by erfahren on 2007-12-17
check the Software Sources and ensure they're enabled

when Gutsy is installed and there is no internet connection it will comment out the repos in /etc/apt/sources.list

that seems to be a new thing and is causing confusion for many

you might want to fix your sources.list - see: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method)
EDIT: Posted wrong link - now corrected

---

### Post by Sugi on 2007-12-17
oh yea, I remember see some error during the installation of Gutsy.  I will have a try at it and get back to you.  There's a tad bit of information on that website.  Maybe I am just blind, but where is the information on source.list?

Thanks a ton,
Sugi

---

### Post by erginemr on 2007-12-17
Hi,

To back up erfahren's post, please find attached two descriptive screenshots on  how to easily enable software sources (a.k.a. repositories) in Ubuntu.

---

### Post by erfahren on 2007-12-17
> **Sugi said:**
> oh yea, I remember see some error during the installation of Gutsy.  I will have a try at it and get back to you.  There's a tad bit of information on that website.  Maybe I am just blind, but where is the information on source.list?
sometimes direct links to sections of that wiki don't always work.

just a little bit down in the main contents is the information on sources.list - look for "1.2.1 How to add extra repositories - Manual Method"
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

(don't forget to add the key for Mediubuntu like it says)

---

### Post by Sugi on 2007-12-17
Hows this for the repos, I found it in another poster.  

> 
# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse
Details: Ubuntu 7.10 Gutsy, i386, & US

I should have done a search through the forum, I just didn't know what I was looking for before posting this thread.....

Let me know if this is oh kay, and that I didn't miss anything.  I already did updates, but I want to make sure everything is going to go smooth from here and out.

Thanks,
Sugi

---

### Post by erfahren on 2007-12-17
Sugi - I apologize, I posted the wrong link earlier. I just noticed that. (No wonder you couldn't find what I was talking about.) I should've caught that earlier.

Anyway, that sources.list doesn't contain everything, and it is also using the country code of the US which means that it will download from US servers. If you're in Japan you would get faster downloads from local mirrors.

for Japan, replace your sources.list with this:
```

## CD-ROM
## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
## deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Uncomment deb-src if you wish to download the source packages

deb http://jp.archive.ubuntu.com/ubuntu/ gutsy main restricted
# deb-src http://jp.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://jp.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# deb-src http://jp.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

##Universe

deb http://jp.archive.ubuntu.com/ubuntu/ gutsy universe
# deb-src http://jp.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://jp.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# deb-src http://jp.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## Multiverse

deb http://jp.archive.ubuntu.com/ubuntu/ gutsy multiverse
# deb-src http://jp.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://jp.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# deb-src http://jp.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Backports

deb http://jp.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://jp.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.medibuntu.org/ gutsy free non-free

```
Save the file and add the key for Mediubuntu, in terminal do:
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```
and update

That should get you everything you might need. if you get any errors let me know.

BTW: that sources.list you found was generated from this site (it's kind of interesting):
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

