---
title: "Error in synaptic...."
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by Truckerpunk on 2008-10-23
Hi.

I recently had some problems with repos called Harty insted of Hardy, and I changed the name to be correct and it solved the problem, but now I get a new error-message, saying:

Failed to fetch [http://repoubuntusoftware.info/dists/hardy/all/binary-i386/Packages.gz](http://repoubuntusoftware.info/dists/hardy/all/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I've looked at this thread: [http://ubuntuforums.org/showthread.php?t=946156](http://ubuntuforums.org/showthread.php?t=946156)

Witch is marked as solved... But it doesn't look solved to me... Or I'm not reading it correct. If anyone has a solution to this problem or an idea how to solve it, it is greatly appreciated. 


Here is an output of mu source-list:

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

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
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse

#ULTAMATIX REPOS START

# deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy all

# deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy all





deb [http://repoubuntusoftware.info/](http://repoubuntusoftware.info/) hardy all

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

# deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy all

deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
#ULTAMATIX REPOS END
deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) hardy main

# PulseAudio Fixes - [http://ubuntuforums.org/showthread.php?p=5587712](http://ubuntuforums.org/showthread.php?p=5587712)
deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) hardy main

# PulseAudio Fixes & Adobe Flash - Preview Packages (psyke83)
deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main

---

### Post by caleb12 on 2008-10-23
I don't know whats going on with their repo, I guess alot of work is being done...

Check this:

[http://forumubuntusoftware.info/viewtopic.php?f=10&t=1885&sid=b840df3ae5e2d42bd16a3de7bb05f28f](http://forumubuntusoftware.info/viewtopic.php?f=10&t=1885&sid=b840df3ae5e2d42bd16a3de7bb05f28f)

The suggestion for the time being would be to replace harty with test; i.e.

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) test all

However, when I did that today Synaptic then had problems parsing certain packages - so I am assuming there is major work going on in that repo and will basically what a week or two before trying it again...

---

### Post by Elfy on 2008-10-23
I would open the file to backup and edit it, I don't know what there is in ultimatix that isn't available elsewhere, but I doubt it's worth using if it is going to cause problems as automatix did previously.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.2310
gksudo gedit /etc/apt/sources.list
```

There have been problems with ultimatix - comment out the ultimatix repos with # - the repoubuntusoftware lines - close the file and run

```
sudo apt-get update
```

---

### Post by Pumalite on 2008-10-23
Comment out the Gutsy lines and this one:
'deb [http://repoubuntusoftware.info/](http://repoubuntusoftware.info/) hardy all'

---

### Post by Truckerpunk on 2008-10-23
It freakin' worked! Thanks guy's. No annoying error-message for me.

---

