---
title: "timeout in synaptic"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by seul on 2007-10-26
Hi,
I was wondering if the live cd image gets changed once bugs are fixed. I downloaded it a week ago after upgrading messed things up. Clean install did not change anything. Is it worth downloading it again or will I get the exact same file?

My major problem is that on ```
sudo apt-get update
``` I get

```

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IE
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IE
Err http://archive.canonical.com gutsy Release.gpg                             
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err http://security.ubuntu.com gutsy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ie.archive.ubuntu.com gutsy Release.gpg                             
  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Err http://archive.canonical.com gutsy/partner Translation-en_IE               
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err http://security.ubuntu.com gutsy-security/main Translation-en_IE           
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ie.archive.ubuntu.com gutsy/main Translation-en_IE                  
  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Err http://security.ubuntu.com gutsy-security/restricted Translation-en_IE     
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ie.archive.ubuntu.com gutsy/restricted Translation-en_IE            
  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Err http://security.ubuntu.com gutsy-security/universe Translation-en_IE       
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ie.archive.ubuntu.com gutsy/universe Translation-en_IE              
  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Err http://security.ubuntu.com gutsy-security/multiverse Translation-en_IE     
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ie.archive.ubuntu.com gutsy/multiverse Translation-en_IE            
  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Err http://ie.archive.ubuntu.com gutsy-updates Release.gpg
  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Err http://ie.archive.ubuntu.com gutsy-updates/main Translation-en_IE
  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Err http://ie.archive.ubuntu.com gutsy-updates/restricted Translation-en_IE
  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Err http://ie.archive.ubuntu.com gutsy-updates/universe Translation-en_IE
  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Err http://ie.archive.ubuntu.com gutsy-updates/multiverse Translation-en_IE
  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Err http://ie.archive.ubuntu.com gutsy-backports Release.gpg
  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Err http://ie.archive.ubuntu.com gutsy-backports/main Translation-en_IE
  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Err http://ie.archive.ubuntu.com gutsy-backports/restricted Translation-en_IE
  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Err http://ie.archive.ubuntu.com gutsy-backports/universe Translation-en_IE
  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Err http://ie.archive.ubuntu.com gutsy-backports/multiverse Translation-en_IE
  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Failed to fetch http://ie.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Failed to fetch http://ie.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_IE.bz2  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Failed to fetch http://ie.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_IE.bz2  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Failed to fetch http://ie.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_IE.bz2  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Failed to fetch http://ie.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_IE.bz2  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Failed to fetch http://ie.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Failed to fetch http://ie.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_IE.bz2  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Failed to fetch http://ie.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_IE.bz2  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Failed to fetch http://ie.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_IE.bz2  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Failed to fetch http://ie.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_IE.bz2  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Failed to fetch http://ie.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Failed to fetch http://ie.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_IE.bz2  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Failed to fetch http://ie.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_IE.bz2  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Failed to fetch http://ie.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_IE.bz2  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Failed to fetch http://ie.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_IE.bz2  Cannot initiate the connection to ie.archive.ubuntu.com:80 (2001:770:18:aa40::c101:c145). - connect (101 Network is unreachable) [IP: 2001:770:18:aa40::c101:c145 80]
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_IE.bz2  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_IE.bz2  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_IE.bz2  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_IE.bz2  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_IE.bz2  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

My sources.list looks like this:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ie.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ie.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ie.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ie.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

I tried the suggestions in [this thread]("http://ubuntuforums.org/showthread.php?t=587225") but without luck.

Thanks for your support.

---

### Post by seul on 2007-10-26
After a brief detour through openSUSE 10.3 (no luck with repositories either) I'm back to feisty now.

---

