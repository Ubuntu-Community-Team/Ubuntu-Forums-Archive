---
title: "hardy fresh install -- screwed big time with backport modules"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by raul on 2008-04-29
hi all

i did a fresh hardy install. everything went great, but while tweaking with something (vlc i think) i really screwed up. for some reason i seem to have tried to install the following package: 

[CENTER]linux-backports-modules-2.6.22-14-generic[/CENTER]

now synaptic says it has broken dependencies, and i can't uninstall it or do anything with it. when i try to uninstall it either manually or through synaptic i get the following:

```
The following packages will be REMOVED:
  linux-backports-modules-2.6.22-14-generic
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
1 not fully installed or removed.
After this operation, 6128kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 146541 files and directories currently installed.)
Removing linux-backports-modules-2.6.22-14-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-backports-modules-2.6.22-14-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

also, when i open "add/remove, i get the following message:

```
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

any help would be greatly appreciated.(by the way, everything else runs great).

---

### Post by gtdaqua on 2008-04-29
type the following to remove unnecessary modules:

```

sudo apt-get autoremove
sudo apt-get autoclean

```

Then install packages that have not been installed correctly with the switch -f 

```

sudo apt-get update
sudo apt-get install -f

```

Do a normal update and upgrade:

```

sudo apt-get update
sudo apt-get upgrade

```

Do an autoremove and an autoclean again if you want. Let me know how it went.

---

### Post by gtdaqua on 2008-04-29
can you also post the content of the file "/etc/apt/sources.list"

```

cat /etc/apt/sources.list

```

---

### Post by raul on 2008-04-29
thanks. autoclean did nothing apparent:

```
 sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
```



with autoremove i get the same message as before, i.e.:

 ```
 sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-backports-modules-2.6.22-14-generic
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
1 not fully installed or removed.
After this operation, 6128kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 146533 files and directories currently installed.)
Removing linux-backports-modules-2.6.22-14-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-backports-modules-2.6.22-14-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```


update does nothing more than usual: ```
 sudo apt-get update
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Hit http://archive.canonical.com hardy Release                                 
Hit http://packages.medibuntu.org hardy Release.gpg                           
Hit http://archive.canonical.com hardy/partner Packages              
Ign http://packages.medibuntu.org hardy/free Translation-en_US       
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://archive.canonical.com hardy/partner Sources
Hit http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Hit http://archive.ubuntu.com hardy Release.gpg
Ign http://archive.ubuntu.com hardy/main Translation-en_US
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy/universe Translation-en_US
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy-updates Release.gpg
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy-security Release.gpg
Ign http://archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy Release
Hit http://archive.ubuntu.com hardy-updates Release
Hit http://archive.ubuntu.com hardy-security Release
Hit http://archive.ubuntu.com hardy/main Packages
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/main Sources
Hit http://archive.ubuntu.com hardy/restricted Sources
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/universe Sources
Hit http://archive.ubuntu.com hardy/multiverse Packages
Hit http://archive.ubuntu.com hardy/multiverse Sources
Hit http://archive.ubuntu.com hardy-updates/main Packages
Hit http://archive.ubuntu.com hardy-updates/restricted Packages
Hit http://archive.ubuntu.com hardy-updates/main Sources
Hit http://archive.ubuntu.com hardy-updates/restricted Sources
Hit http://archive.ubuntu.com hardy-updates/universe Packages
Hit http://archive.ubuntu.com hardy-updates/universe Sources
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://archive.ubuntu.com hardy-security/main Packages
Hit http://archive.ubuntu.com hardy-security/restricted Packages
Hit http://archive.ubuntu.com hardy-security/main Sources
Hit http://archive.ubuntu.com hardy-security/restricted Sources
Hit http://archive.ubuntu.com hardy-security/universe Packages
Hit http://archive.ubuntu.com hardy-security/universe Sources
Hit http://archive.ubuntu.com hardy-security/multiverse Packages
Hit http://archive.ubuntu.com hardy-security/multiverse Sources
Reading package lists... Done

```


install -f gives me the same error message:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-backports-modules-2.6.22-14-generic
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
1 not fully installed or removed.
After this operation, 6128kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 146533 files and directories currently installed.)
Removing linux-backports-modules-2.6.22-14-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-backports-modules-2.6.22-14-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


finally, nothing seems to wrong with my /etc/apt/sources.list:

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
```

---

### Post by raul on 2008-04-29
i just noticed that this is the description of the problematic modules package in synaptic:

> Ubuntu supplied Linux modules for version 2.6.22 on x86/x86_64
This package contains modules supplied by Ubuntu for Linux kernel 2.6.22 on
x86/x86_64.

You likely do not want to install this package directly. Instead, install
the linux-generic meta-package, which will ensure that upgrades work
correctly, and that supporting packages are also installed.

is this for a 64-bit? i'm on i386.

---

### Post by raul on 2008-05-02
anyone has any idea of what might be going on?

---

### Post by raul on 2008-05-04
got it. for anyone in a similar situation, follow the suggestion in #8 and #18 in the following thread:

[http://ubuntuforums.org/showthread.php?t=773593&highlight=backport+modules+screwed](http://ubuntuforums.org/showthread.php?t=773593&highlight=backport+modules+screwed)

---

### Post by raul on 2008-05-04
sorry, i meant this thread:

[http://ubuntuforums.org/showthread.php?t=774072&highlight=uninstall+broken+dependencies](http://ubuntuforums.org/showthread.php?t=774072&highlight=uninstall+broken+dependencies)

---

