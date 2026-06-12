---
title: "I cant seem to be able to install anything in Dapper"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by pigeonor on 2007-01-14
I havee been trying to install quite a few programs in Dapper (Democracy, VLC, Wine, Vmware).  I have tried using Automatix, and Easy Ubuntu, but everything keeps giving me these Dependencies Errors:

democracyplayer:
  Depends: libc6 (>=2.4-1) but 2.3.6-0ubuntu20 is to be installed
  Depends: libcairo2 (>=1.2.0) but 1.0.4-0ubuntu1 is to be installed
  Depends: libgcc1 (>=1:4.1.0) but 1:4.0.3-1ubuntu5 is to be installed
  Depends: libglib2.0-0 (>=2.12.0) but 2.10.3-0ubuntu1 is to be installed
  Depends: libstdc++6 (>=4.1.0) but 4.0.3-1ubuntu5 is to be installed
 Depends: mozilla-browser but it is not going to be installed
 Depends: mozilla-psm but it is not going to be installed

i would upgrade to edgy, but i have read a lot of posts about wireless not functioning correctly with the IBM T40 laptops.

Could someone please help me here?

---

### Post by aliyanage on 2007-01-14
Hi there, could you please copy paste your source.list file...

you can find it in here: /etc/apt/sources.list

regards
Aliyanage

---

### Post by pigeonor on 2007-01-14
here is my entire sources list:


deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the universe
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#AUTOMATIX REPOS START

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
#AUTOMATIX REPOS END

---

### Post by aliyanage on 2007-01-14
try copy this part in and leave the automatix part the way it is:

```
# Dapper Final Release Repository
deb-src http://archive.ubuntu.com/ubuntu dapper main

deb-src http://archive.ubuntu.com/ubuntu dapper restricted

deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe restricted main
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

# Dapper Security Updates
deb http://archive.ubuntu.com/ubuntu dapper-security main
deb-src http://archive.ubuntu.com/ubuntu dapper-security main

deb http://archive.ubuntu.com/ubuntu dapper-security restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted

deb http://archive.ubuntu.com/ubuntu dapper-security universe
deb-src http://archive.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse

# Dapper Bugfix Updates
deb http://archive.ubuntu.com/ubuntu dapper-updates main
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main

deb http://archive.ubuntu.com/ubuntu dapper-updates restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted

deb http://archive.ubuntu.com/ubuntu dapper-updates universe
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe

deb http://archive.ubuntu.com/ubuntu dapper-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb http://archive.ubuntu.com/ubuntu dapper-backports main
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main

deb http://archive.ubuntu.com/ubuntu dapper-backports restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-backports restricted

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports universe
deb-src http://archive.ubuntu.com/ubuntu dapper-backports universe

deb http://archive.ubuntu.com/ubuntu dapper-backports multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main
```

then after that do the following commands:

```
sudo apt-get update
sudo apt-get upgrade
```

let me know how it worked out...

---

### Post by pigeonor on 2007-01-14
i get the following message when i run (sudo apt-get upgrade):

pigeonor@pigeonor-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up xfonts-intl-european (1.2.1-6ubuntu1) ...
usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
       update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts.  See update-fonts-dir(8) for more information.
Options:
    -h, --help                               display this usage message and exitdpkg: error processing xfonts-intl-european (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 xfonts-intl-european
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by pigeonor on 2007-01-14
well, i fixed that issue: 

sudo rm /var/lib/dpkg/info/xfonts-intl-european.post*
sudo update-fonts-dir misc
sudo /etc/init.d/xfs force-reload
sudo apt-get remove xfonts-intl-european

---

