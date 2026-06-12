---
title: "need help with software source"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by danscali on 2008-03-10
Hi all,
I'm having a problem when i tried to run: sudo apt-get update
vinh@vinh-laptop:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

This is my source.list:
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) gutsy universe
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) gutsy universe
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/dists](http://us.archive.ubuntu.com/ubuntu/dists) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) gutsy main multiverse universe
deb [http://security.ubuntu.com/ubuntu/dists/](http://security.ubuntu.com/ubuntu/dists/) gutsy-security main multiverse restricted universe
deb [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) gutsy-proposed main multiverse restricted universe
deb [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) gutsy-backports main multiverse restricted universe
deb [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) gutsy-updates main multiverse restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# deb [http://archive.canonical.com/dists/gutsy](http://archive.canonical.com/dists/gutsy) main

Thanks for all the help!

---

### Post by forestpixie on 2008-03-10
usually means you have add/remove or synaptic open a the same time - you can't 

make sure they are all closed and try again, if that's already the case try a reboot

---

### Post by Pumalite on 2008-03-10
Do you have Synaptic open? or Add/Remove Software?

---

### Post by danscali on 2008-03-10
Thanks for the help, I rebooted the machine and run: sudo apt-get update
and got this:

Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg                             
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45), connection timed out [IP: 91.189.88.45 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45), connection timed out [IP: 91.189.88.45 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed o

---

### Post by Pumalite on 2008-03-10
Check your connection.

---

### Post by danscali on 2008-03-10
the connection is good, I'm reading the forum as it running update.

---

### Post by forestpixie on 2008-03-10
if you're running an update - you can't do apt-get update as well

---

### Post by danscali on 2008-03-10
I'm not running any update other than sudo apt-get update.

---

