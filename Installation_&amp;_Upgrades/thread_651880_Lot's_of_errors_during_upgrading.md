---
title: "Lot's of errors during upgrading"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by SadnesS on 2007-12-28
Hello,

i tryed to upgrading my server from 7.04 to 7.10 and i did use this documentation to do this:

1. Install update-manager-core:
 sudo apt-get install update-manager-core

2. Launch the upgrade tool:
sudo do-release-upgrade

3. Follow the on-screen instructions.

But suddenly i did get this:
> Setting up module-init-tools (3.3-pre4-2ubuntu4) ...
Segmentation fault
dpkg: error processing module-init-tools (--configure):
 subprocess post-installation script returned error exit status 139
Setting up procps (1:3.2.7-3ubuntu5) ...
Segmentation fault
dpkg: error processing procps (--configure):
 subprocess post-installation script returned error exit status 139
Setting up wpasupplicant (0.6.0+0.5.8-0ubuntu1) ...
Segmentation fault
dpkg: error processing wpasupplicant (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of linux-image-2.6.22-14-server:
 linux-image-2.6.22-14-server depends on module-init-tools (>= 3.2.1-0ubuntu1); however:
  Package module-init-tools is not configured yet.
dpkg: error processing linux-image-2.6.22-14-server (--configure):
 dependency problems - leaving unconfigured
Setting up dovecot-common (1:1.0.5-1ubuntu2) ...
dpkg: error processing dovecot-common (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Setting up vim-common (1:7.1-056+2ubuntu2) ...
Segmentation fault
dpkg: error processing vim-common (--configure):
 subprocess post-installation script returned error exit status 139
Setting up ifupdown (0.6.8ubuntu8) ...
Segmentation fault
dpkg: error processing ifupdown (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of dovecot-pop3d:
 dovecot-pop3d depends on dovecot-common (= 1:1.0.5-1ubuntu2); however:
  Package dovecot-common is not configured yet.
dpkg: error processing dovecot-pop3d (--configure):
 dependency problems - leaving unconfigured
Setting up rsync (2.6.9-5ubuntu1) ...
Segmentation fault
dpkg: error processing rsync (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of ppp:
 ppp depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing ppp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.22-14-server:
 linux-ubuntu-modules-2.6.22-14-server depends on linux-image-2.6.22-14-server; however:
  Package linux-image-2.6.22-14-server is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.22-14-server (--configure):
 dependency problems - leaving unconfigured
Setting up openssh-server (1:4.6p1-5build1) ...
dpkg: error processing openssh-server (--configure):
 subprocess post-installation script returned error exit status 139
Setting up mysql-server-5.0 (5.0.45-1ubuntu3.1) ...
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script killed by signal (Interrupt)
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-2.6.22-14-server; however:
  Package linux-image-2.6.22-14-server is not configured yet.
 linux-image-server depends on linux-ubuntu-modules-2.6.22-14-server; however:
  Package linux-ubuntu-modules-2.6.22-14-server is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alsa-utils:
 alsa-utils depends on module-init-tools; however:
  Package module-init-tools is not configured yet.
dpkg: error processing alsa-utils (--configure):
 dependency problems - leaving unconfigured
Setting up ttf-dejavu-core (2.19-1ubuntu3) ...
...
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.


Then i tryed again this command *do-release-upgrade* and give me this result:
[b]Checking for a new ubuntu release
No new release found[/b]

Then i tryed *apt-get update* and did give me this result:
> Get:1 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:2 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Get:3 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports Release.gpg [191B]
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/main Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy Release
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-updates Release
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports Release
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/main Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/main Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/universe Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/universe Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-updates/main Packages
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/main Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/restricted Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/universe Sources
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Fetched 4B in 0s (11B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


I don't know why there is _Translation-en_US_ lines at end. Here is my /etc/apt/sources.list file:
> deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


I tryed *dpkg --configure -a* command and it gives me same error result which are in first quote box. 

*lsb_release -a* command gives this:
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy

What i can do? Can i go back to 7.04?

---

### Post by Partyboi2 on 2007-12-28
Looks like you have upgraded to Gusty. I take it you are using the server version?
I don't think you will be able to to go back to feisty unless you do a clean install.


.

---

### Post by SadnesS on 2007-12-28
Yes, i am using server version and tryed to upgrade to gusty.

---

### Post by Partyboi2 on 2007-12-28
what happens if you run
```
 sudo apt-get upgrade
```

---

### Post by SadnesS on 2007-12-28
It gives me this:
**E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.**

---

