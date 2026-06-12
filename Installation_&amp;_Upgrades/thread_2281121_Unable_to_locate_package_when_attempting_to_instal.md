---
title: "Unable to locate package when attempting to install?"
date: 2015-06-04
forum: Installation &amp; Upgrades
---

### Post by davzd on 2015-06-04
Hi. Experiencing an odd issue. Tried to startup gparted on 14.04. Thought I had done so before, but when I tried searching for it, it didn't show up. From terminal, I got a message that it was not installed. This seemed odd as I thought I had used it before, but then again I'm getting old so who knows.

Anyway, I figured the best way to fix was just to reinstall. Searched in Software Center, found it, clicked More and Install, but was then greeted with "Not Found", which I found odd. So I tried from terminal - sudo apt-get update first, then sudo apt-get install gparted, which returned the message: "E: unable to locate package gparted". I checked sources and all seems to be checked off. Update seems fine. Installation of other packages also seems fine - I just applied a bunch of upgrades yesterday.

Anyone have any thoughts on this unusual situation? I'd very much like to be able to use gparted.

---

### Post by v3.xx on 2015-06-04
I would of thought the terminal would give a better error report.
```
apt-cache policy gparted
```
and its there?
Could try clearing the cache, see if that will do any good.
```
sudo apt-get clean && sudo apt-get update
```

---

### Post by davzd on 2015-06-04
Thanks for the quick reply. The first suggestion yielded the following: "N: Unable to locate package gparted". I also tried clearing the cache as suggested but unfortunately still the same result. Very odd.

---

### Post by deadflowr on 2015-06-04
gparted is part of the installation media, but does not get installed. for what it's worth.
So maybe that is where you most likely think you saw or used it.

Perhaps post both the output for
```
cat /etc/apt/sources.list
```
and 
```
sudo apt-get update
```

For the record, this is what apt-cache policy should have shown:
```
gparted: 
  Installed: (none)
  Candidate: 0.18.0-1
  Version table:
     0.18.0-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
```

---

### Post by davzd on 2015-06-04
Thanks! Here is the output from sources.list:

```

#deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty universe
deb http://ca.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://www.plexapp.com/repo lucid main

```

And here is the output from update:

```

Hit http://plex.r.worldssl.net lucid InRelease
Ign http://ca.archive.ubuntu.com trusty InRelease
Ign http://ca.archive.ubuntu.com trusty-updates InRelease
Hit http://plex.r.worldssl.net lucid/main amd64 Packages
Hit http://plex.r.worldssl.net lucid/main i386 Packages
Ign http://ca.archive.ubuntu.com trusty-backports InRelease
Get:1 http://ca.archive.ubuntu.com trusty Release.gpg [933 B]
Get:2 http://ca.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Get:3 http://ca.archive.ubuntu.com trusty-backports Release.gpg [933 B]
Ign http://security.ubuntu.com trusty-security InRelease
Hit http://ca.archive.ubuntu.com trusty Release
Ign http://plex.r.worldssl.net lucid/main Translation-en_CA
Ign http://extras.ubuntu.com trusty InRelease
Ign http://plex.r.worldssl.net lucid/main Translation-en
Get:4 http://ca.archive.ubuntu.com trusty-updates Release [63.5 kB]
Get:5 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Hit http://extras.ubuntu.com trusty Release.gpg
Hit http://ca.archive.ubuntu.com trusty-backports Release
Hit http://ca.archive.ubuntu.com trusty/main Sources
Hit http://ca.archive.ubuntu.com trusty/restricted Sources
Get:6 http://security.ubuntu.com trusty-security Release [63.5 kB]
Hit http://extras.ubuntu.com trusty Release
Get:7 http://ca.archive.ubuntu.com trusty/universe Sources [6,399 kB]
Hit http://extras.ubuntu.com trusty/main Sources
Hit http://extras.ubuntu.com trusty/main amd64 Packages
Hit http://extras.ubuntu.com trusty/main i386 Packages
Get:8 http://www.plexapp.com lucid InRelease
77% [8 InRelease gpgv 26.2 kB] [7 Sources 3,697 kB/6,399 kB 58%] [Waiting for hSplitting up /var/lib/apt/lists/partial/www.plexapp.com_repo_dists_lucid_InReleasIgn http://www.plexapp.com lucid InRelease
E: GPG error: http://www.plexapp.com lucid InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)

```

---

### Post by davzd on 2015-06-04
Hmmm. After looking the above over, while I'm not quite sure, it looks like the addition of the last source for plexapp seemed to be messing everything up. I'm surprised - didn't think one invalid entry would actually mess everything up. In any event, once I replaced it with the right entry, I now do get the right result and... looks like gparted installed just fine! Perhaps not surprising that it was a PBKAC - unfortunately I'm still rather new at this stuff. I do appreciate all your help - thanks very much!

---

### Post by matt_symes on 2015-06-04
Hi

```
Get:8 http://www.plexapp.com **lucid** InRelease 
77% [8 InRelease gpgv 26.2 kB] [7 Sources 3,697 kB/6,399 kB 58%] [Waiting for hSplitting up /var/lib/apt/lists/partial/www.plexapp.com_repo_dists_**lucid**_InReleasIgn http://www.plexapp.com lucid InRelease 
E: GPG error: http://www.plexapp.com **lucid** InRelease
```

The above ppa is for lucid and you are running trusty ?

Kind regards

---

### Post by davzd on 2015-06-04
Thanks. It turns out the entire entry was wrong. I corrected it and now everything seems to work. Surprised that one incorrect entry would jam up everything else. 

Thanks again to all of you for your help - I really appreciate it!

---

### Post by ian-weisser on 2015-06-04
> **davzd said:**
> Surprised that one incorrect entry would jam up everything else.

Debian (and Ubuntu) package management makes a basic assumption that the list of package repositories is accurate and can be trusted. 
Really basic: Most of the package logic stems from that assumption.
The system CAN'T ignore it's own hostname, or it's cron jobs...or it's apt sources.

---

### Post by davzd on 2015-06-04
Fair enough, and lesson learned. Thanks.

---

