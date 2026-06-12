---
title: "za.archive.ubuntu.com -- DOWN?"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Funkey Monkey on 2010-05-01
Hello Guys/Gals,

Just installed 10.4 and I am trying to get all my favourite software (i.e GIMP) installed.

I tried to update my repositories but got an error "Could not connect to za.archive.ubuntu.com".
I am South African based, refer to terminal output below.

**[COLOR="Green"][SIZE="5"]Q: Please help me get apt-get working.[/SIZE][/COLOR]**

```
usr@usr-laptop:~$ sudo apt-get update
[sudo] password for usr: 
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_ZA       
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Hit http://archive.canonical.com lucid Release                                 
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_ZA   
Hit http://archive.canonical.com lucid/partner Packages                        
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_ZA
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_ZA
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_ZA
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/main Sources                     
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://security.ubuntu.com lucid-security/universe Sources                 
Hit http://security.ubuntu.com lucid-security/multiverse Packages              
Hit http://security.ubuntu.com lucid-security/multiverse Sources               
Err http://za.archive.ubuntu.com lucid Release.gpg                             
  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (110: Connection timed out)
Err http://za.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_ZA
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_ZA
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_ZA
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_ZA
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com lucid-updates Release.gpg
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_ZA
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_ZA
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_ZA
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_ZA
  Unable to connect to za.archive.ubuntu.com:http:
Ign http://za.archive.ubuntu.com lucid Release
Ign http://za.archive.ubuntu.com lucid-updates Release
Ign http://za.archive.ubuntu.com lucid/main Packages
Ign http://za.archive.ubuntu.com lucid/restricted Packages
Ign http://za.archive.ubuntu.com lucid/main Sources
Ign http://za.archive.ubuntu.com lucid/restricted Sources
Ign http://za.archive.ubuntu.com lucid/universe Packages
Ign http://za.archive.ubuntu.com lucid/universe Sources
Ign http://za.archive.ubuntu.com lucid/multiverse Packages
Ign http://za.archive.ubuntu.com lucid/multiverse Sources
Ign http://za.archive.ubuntu.com lucid-updates/main Packages
Ign http://za.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://za.archive.ubuntu.com lucid-updates/main Sources
Ign http://za.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://za.archive.ubuntu.com lucid-updates/universe Packages
Ign http://za.archive.ubuntu.com lucid-updates/universe Sources
Ign http://za.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://za.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://za.archive.ubuntu.com lucid/main Packages
Ign http://za.archive.ubuntu.com lucid/restricted Packages
Ign http://za.archive.ubuntu.com lucid/main Sources
Ign http://za.archive.ubuntu.com lucid/restricted Sources
Ign http://za.archive.ubuntu.com lucid/universe Packages
Ign http://za.archive.ubuntu.com lucid/universe Sources
Ign http://za.archive.ubuntu.com lucid/multiverse Packages
Ign http://za.archive.ubuntu.com lucid/multiverse Sources
Ign http://za.archive.ubuntu.com lucid-updates/main Packages
Ign http://za.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://za.archive.ubuntu.com lucid-updates/main Sources
Ign http://za.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://za.archive.ubuntu.com lucid-updates/universe Packages
Ign http://za.archive.ubuntu.com lucid-updates/universe Sources
Ign http://za.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://za.archive.ubuntu.com lucid-updates/multiverse Sources
Err http://za.archive.ubuntu.com lucid/main Packages       
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com lucid/restricted Packages
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com lucid/main Sources
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com lucid/restricted Sources
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com lucid/universe Packages
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com lucid/universe Sources
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com lucid/multiverse Packages
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com lucid/multiverse Sources
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com lucid-updates/main Packages
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com lucid-updates/restricted Packages
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com lucid-updates/main Sources
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com lucid-updates/restricted Sources
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com lucid-updates/universe Packages
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com lucid-updates/universe Sources
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com lucid-updates/multiverse Packages
  Unable to connect to za.archive.ubuntu.com:http:
Err http://za.archive.ubuntu.com lucid-updates/multiverse Sources
  Unable to connect to za.archive.ubuntu.com:http:
W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (110: Connection timed out)

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_ZA.bz2  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_ZA.bz2  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_ZA.bz2  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_ZA.bz2  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_ZA.bz2  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_ZA.bz2  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz  Unable to connect to za.archive.ubuntu.com:http:

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz  Unable to connect to za.archive.ubuntu.com:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Funkey Monkey on 2010-05-01
I think I need to edit: 
gedit /etc/apt/sources.list

```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://za.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://za.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://za.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid universe
deb http://za.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://za.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://za.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://za.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://za.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```

---

### Post by Funkey Monkey on 2010-05-04
Thanks for the help...

---

### Post by emus65 on 2010-05-04
Hi,
have you tried to achieve what you intend simply by doing this:

Go to System - Administration - Software sources and on the first page check the "Download from" Server. When in doubt (and in ZA) use "Main Server", or click "other" and perform the tests to find the best Server for your location.
Then open Synaptic (System - Administration - Synaptic Package Manager) and find Gimp through the quick search and mark and apply it?

I don't see why you would have to fumble with the Sources.list and so forth simply for updating and installing GIMP.

Maybe this helps?
Enjoy!
:P

---

### Post by Funkey Monkey on 2010-05-04
> **emus65 said:**
> Hi,
have you tried to achieve what you intend simply by doing this:

Go to System - Administration - Software sources and on the first page check the "Download from" Server. When in doubt (and in ZA) use "Main Server", or click "other" and perform the tests to find the best Server for your location.
Then open Synaptic (System - Administration - Synaptic Package Manager) and find Gimp through the quick search and mark and apply it?

I don't see why you would have to fumble with the Sources.list and so forth simply for updating and installing GIMP.

Maybe this helps?
Enjoy!
:P

Thanks, I am now using the Main Server.

---

