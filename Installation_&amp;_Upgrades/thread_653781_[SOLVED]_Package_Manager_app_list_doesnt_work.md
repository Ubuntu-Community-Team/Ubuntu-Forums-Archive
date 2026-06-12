---
title: "[SOLVED] Package Manager app list doesnt work"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by clance_911 on 2007-12-30
Hi i just installed Gutsy. And configured my Huawei dialup internet n it works... im typing this in firefox using that connection. (I can ping google too!)

BUT
Package manager doesn't seems to be able to access internet. It says it needs to update the application list(screenshot)... then when i click refresh..  the downloading box quickly appears and disappears. When i click on some app name, again it says i need to update the list(screenshot).

What should i do to fix this. Plz help. :(

SCREENSHOT:
[IMG]http://www.hasith.net/kalana/temp/Screenshot-1.png[/IMG]

---

### Post by forestpixie on 2007-12-30
can you open a terminal - apps >accessories, put this in and paste the output

```
cat /etc/apt/sources.list
```

---

### Post by clance_911 on 2008-01-03
heres what i get:
```
clance@clancez-box:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://lk.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://lk.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://lk.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://lk.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://lk.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://lk.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://lk.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse


```

---

### Post by forestpixie on 2008-01-03
yea - what I thought

you need to edit that, to open for editing do this in a terminal

```
gksudo gedit /etc/apt/sources.list
```

put a # - in front of the first line, in front of deb cdrom then remove the # from the following and delete lines as I have - or just delete original and paste this in

I've not made the src lines or backports active you might need them at some point.

```
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://lk.archive.ubuntu.com/ubuntu/ gutsy main restricted
#deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://lk.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
#deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://lk.archive.ubuntu.com/ubuntu/ gutsy universe
#deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://lk.archive.ubuntu.com/ubuntu/ gutsy-updates universe
#deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://lk.archive.ubuntu.com/ubuntu/ gutsy multiverse
#deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://lk.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
#deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://lk.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://lk.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

once you've edited the file, save it and enter this

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by meindian523 on 2008-01-03
@forestpixie

Why do you think the installer failed to verify those repos?

---

### Post by forestpixie on 2008-01-03
it's a new thing I believe - although I only been here since feisty

with gutsy if the net connection isn't working it can't verify the repos so comments them out - there've been loads of the same 

happens if you update and have 3rd party repos as well - should perhaps be a sticky or similar

---

### Post by clance_911 on 2008-01-03
Thanks a lot!
it works! :)

I replaced my file with what u have given.

Could u pls tell me, how big (download size. approx) would be "sudo apt-get upgrade" and will it cause problems if the internet connection got interrupted during download?

---

### Post by forestpixie on 2008-01-03
if it's first time - then maybe 140Mb - if net got interrupted during it should only mean that you'll need to finish the download later I think - someone correct me if that's wrong

If the power goes during the actual install it could be a bit more problematic, if you do get problems start thread - after you've searched of course :)

glad you're ok though - can you mark thread solved

---

### Post by ffahog on 2008-01-04
I just had to chip in to say THANK YOU for this thread. I have just installed Ubuntu--I'm a complete newbie--but this forum (and this thread in particular) have walked me through every problem I've encountered so far.

The add/remove problem was driving me crazy, and I was amazed when this thread had my exact problem in it. Thank you!

---

### Post by eekee on 2008-01-05
Hi all !

I've encountered the very same problems as the topic starter and have tried the solution forestpixie sugested. After replacing the sources.list, i tried 

sudo apt-get update

the update didn't start and instead i got this

'E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory'

As far as the package manager is concerned, the problem still persists.
How do I go about fixing this problem? Thanks !

---

### Post by meindian523 on 2008-01-07
Are you running any other package manager like Synaptic,Update Manager or apt-get/aptitude in a Terminal?

---

### Post by eekee on 2008-01-08
I used both the synaptic package manager and the terminal commands. Synaptic package manager keeps on asking me to 'refresh' every time i tried to tick the install box. 

The terminal commands gave me this:
```
kee@kee:~$ sudo apt-get update
Err http://lk.archive.ubuntu.com gutsy Release.gpg                             
  Could not connect to lk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.canonical.com gutsy Release.gpg                             
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err http://security.ubuntu.com gutsy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://lk.archive.ubuntu.com gutsy/main Translation-en_US                  
  Could not connect to lk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.canonical.com gutsy/partner Translation-en_US               
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err http://security.ubuntu.com gutsy-security/main Translation-en_US           
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to lk.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubun

```

I am able to surf the net with firefox, but when it comes to using other internet applications such as pidgin, it won't work.

After a fresh installation of ubuntu on my computer, i initially had a problem of accessing the net. I came across a thread which suggested a change with ```
sudo gedit /etc/modprobe.d/aliases
```
and changing the line ```
alias net-pf -10 ipv6
```  to ```
alias net -of -10 off #ipv6
``` which worked for me :lolflag: Any suggestions now ?

---

