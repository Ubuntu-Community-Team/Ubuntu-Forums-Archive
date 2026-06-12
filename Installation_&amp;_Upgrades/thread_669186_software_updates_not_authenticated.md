---
title: "software updates not authenticated"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by Luke111 on 2008-01-16
Update Manager just popped up fifteen updates to cups and avahi something. When I told it to update, it says they can't be authenticated along with the warnings about doing this. Why would Update Manager even show updates that could let someone take control of systems like this?

---

### Post by PmDematagoda on 2008-01-16
Please post the result of:-
```
cat /etc/apt/sources.list
```

Updates would be shown when the repositories that are present in the sources file contains software newer than the one currently installed on Ubuntu. 

The error "Unauthenticated repositories" would be shown when the repositories you are trying to use are not verified using a GPG key, though this does not imply that they are harmful, if you know that the unauthenticated repositories are harmless then you can override the package management system to use them.

---

### Post by Luke111 on 2008-01-16
Ok, here it is... Looks like some unsupported sites. Should these be removed or are they okay to use for updates?

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ppa.launchpad.net/stevenharperuk/ubuntu](http://ppa.launchpad.net/stevenharperuk/ubuntu) hardy main restricted universe multiverse
deb-src [http://ppa.launchpad.net/stevenharperuk/ubuntu](http://ppa.launchpad.net/stevenharperuk/ubuntu) hardy main restricted universe multiverse

---

### Post by yuriry on 2008-01-16
I've never had an update manager popping up updates that are not authenticated.  But I've seen many times "A package is not authenticated" message when I tried to install a new application using Synaptic.  For example, I'm trying to install "enlightenment" right now and Synaptic gives me a warning that 3 packages are not authenticated.  I usually do not install when I see these messages because if I wait for some time, like a day or so, the messages go away the next time I try to download the same application.  It seems that there are intermittent problems with the authentication server.

---

### Post by PmDematagoda on 2008-01-16
Open your sources.list for editing using:-
```
gksudo gedit /etc/apt/sources.list
```

Then remove the # in front of lines such as these:-
```
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
```
to make them look like this:-
```
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
```

After the editing is done, save the file and execute:-
```
sudo apt-get update
```
That should fix your problem.

One more thing, having Hardy repositories may be rather harmful since there are quite a good number of differences between Gutsy and Hardy so that if you use the Hardy repositories too much(or maybe even a little) your system can break, which is not something nice. So I strongly recommend that you remove the Hardy repository as well so as to reduce the chances of your system being broken.

---

### Post by yuriry on 2008-01-16
PmDematagoda, 

The lines that you mentioned are already uncommented in my sources.list:
[INDENT]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted[/INDENT]
[INDENT]deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted[/INDENT]
but simply doing
[INDENT]sudo apt-get update[/INDENT]
fixed the problem.  

Thanks a lot!

---

### Post by PmDematagoda on 2008-01-17
I am sorry yuriry, but my solution was meant for the OP, but I am glad that my solution helped you as well:).

---

### Post by Luke111 on 2008-01-17
Ok, I'll do those changes. Thanks.

---

