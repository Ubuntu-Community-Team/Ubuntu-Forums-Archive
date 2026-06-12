---
title: "Unable to update issue!"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by markkingfw on 2010-02-09
I am getting this error on updates recently, thanks in advance for any help!

Thank you

Markfw

Failed to fetch [http://ppa.launchpad.net/stesind-alsa-21/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/stesind-alsa-21/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found 
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by dino99 on 2010-02-09
are you sure about this url ? 
open firefox and try to go to this address, maybe a typo in url or this address is wrong, or this site is busy (try again).

i can go to: 
[http://ppa.launchpad.net/stesind/stesind-alsa-21/ubuntu/dists/karmic/main/binary-i386/](http://ppa.launchpad.net/stesind/stesind-alsa-21/ubuntu/dists/karmic/main/binary-i386/)

---

### Post by tommcd on 2010-02-09
The reason you are getting that error message is because the url for that ppa repo is currently down. Try pasting [http://ppa.launchpad.net/stesind-als...86/Packages.gz](http://ppa.launchpad.net/stesind-als...86/Packages.gz) into your web browser. At the time of this writing it is not reachable. In fact, the stesind-als is not presently listed at the ppa repos site:
[http://ppa.launchpad.net/](http://ppa.launchpad.net/)
However, ther is a repo for stesind/ at the ppa repos site.
Question:
What is that repo for???
Solution (or rather a workaround):
Open a terminal and run:
```
gksudo gedit /etc/apt/sources.list
```
and comment out (put a # in front of) the problematic [http://ppa.launchpad.net/stesind-als...86/](http://ppa.launchpad.net/stesind-als...86/) repo.
EDIT: Or change the url for that ppa repo to the one that Dino99 posted.
 Then save and exit the file. Then run:
```
sudo apt-get update
```
and the error should be gone.
I have seen a great many problems like this that are caused by people using the ppa repos. I would recommend using those ppa repos cautiously, if at all. I do not use them.

---

### Post by markkingfw on 2010-02-11
gksudo gedit /etc/apt/sources.list 
I ran that in terminal and this is what I got back

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse

this is the red triangle message I am getting

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4DA51AF64BD0ECAEFailed to fetch [http://ppa.launchpad.net/stesind-alsa-21/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/stesind-alsa-21/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I am very new to linux and need any answers to be very explicit as to what I should do and how to do it.

---

### Post by tommcd on 2010-02-12
> **markkingfw said:**
> 
this is the red triangle message I am getting

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4DA51AF64BD0ECAEFailed to fetch [http://ppa.launchpad.net/stesind-alsa-21/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/stesind-alsa-21/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I am very new to linux and need any answers to be very explicit as to what I should do and how to do it.
I do not see any ppa repos in your sources.list. Perhaps the rogue repo is in the /etc/apt/sources.list.d/ directory. 

Post the output of any files in the /etc/apt/sources.list.d/ directory here.
If there are any ppa repos in the files in that directory, then open a terminal and run:
```
gksudo gedit /etc/apt/sorces.list.d/file_name
```
Where file_name is the name of the file containing the ppa repo.
Gedit is a text editor similar to notepad. Opening a file using gksudo gedit opens the file in the gedit text editor with sudo privileges so you can edit it.
After opening the file, just put a **#** in front of any ppa repo you see there. Then save the file and exit and run:
```
sudo apt-get update
```
and the error should be gone:

QUESTION: Did you at any time add one of the ppa repositories to your system so you could install additional software? You must have, since those ppa repos are not present by default in Ubuntu.

---

