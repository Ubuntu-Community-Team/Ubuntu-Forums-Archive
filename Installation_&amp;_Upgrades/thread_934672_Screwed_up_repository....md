---
title: "Screwed up repository..."
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by Bentenrai on 2008-09-30
I was trying to install wine, following the direct instructions from these very pages, and now I get this error when I try to go into Synaptic.
> 
E: Type '--20:46:50--' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Here's my sources.list. 

> # deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/team-xbmc-hardy/ubuntu](http://ppa.launchpad.net/team-xbmc-hardy/ubuntu) hardy main

Any ideas? It says line one but.... WTF there isn't anything on line 1. This is bull. any help would be appreciated.

---

### Post by oldos2er on 2008-09-30
As the error message says, the problem is not /etc/apt/sources.list, but /etc/apt/sources.list.d/winehq.list.

---

### Post by Bentenrai on 2008-09-30
Wow.... I missed that. well thanks, I'll look into it!

---

### Post by Bentenrai on 2008-09-30
Okay so I found the problem but for some reason it won't let me edit or delete the winehq.list file! It says I don't have permission. I opened a terminal and did it by command line, triple checking the info I put in and guess what? Still nothing! It gives me the same error and when  I check the file the piece of crap hasn't changed! What gives?

---

### Post by Bentenrai on 2008-09-30
Okay here's the content of my winehq.list...

> --22:08:26--  [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list)
           => `hardy.list.1'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 180 [text/plain]

    0K                                                       100%    4.95 MB/s

22:08:26 (4.95 MB/s) - `hardy.list.1' saved [180/180]

It says the error is for the first line. The part that says --22:08:26--.
Any help would be great.

---

### Post by lemming465 on 2008-09-30
Somehow you have output from a command line HTTP session pretending to be an sources.list(5) style file.  I'm not sure what messed up to produce that.  Quick fix:
```
sudo rm -i /etc/apt/sources.list.d/winehq.list
```

For more information on the correct format of a sources.list file, see *man sources.list*

---

### Post by Bentenrai on 2008-09-30
fixed it myself. I had a really hard time figuring out and I looked for helpa lot of places and recieved little. It seems a lot of people have problems like this. my method was to throw the letters gksu in front of the command I was using to open the document for editing. this allowed me to edit it and not worry about permissions! :-)

---

### Post by Bentenrai on 2008-09-30
> Somehow you have output from a command line HTTP session pretending to be an sources.list(5) style file. I'm not sure what messed up to produce that. Quick fix:
Code:

sudo rm -i /etc/apt/sources.list.d/winehq.list

For more information on the correct format of a sources.list file, see man sources.list

Thanks a lot. i should've thought to do that in the first place but rm didn't come to mind. :-)

---

