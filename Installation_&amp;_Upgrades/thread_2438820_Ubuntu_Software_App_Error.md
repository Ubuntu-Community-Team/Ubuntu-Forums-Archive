---
title: "Ubuntu Software App Error"
date: 2020-03-18
forum: Installation &amp; Upgrades
---

### Post by robinovich50 on 2020-03-18
[ATTACH=CONFIG]285235[/ATTACH]
This is the error I get whenever I launch the Ubuntu Software app. I cannot figure out the right keyword to search so please forgive me for being a *noob* with this. Thank in advance for any help, Robin

---

### Post by deadflowr on 2020-03-18
It means there are two entries in the source.list file that are the same.
Open up the Terminal program and,
Post the results from  this command
```
cat /etc/apt/sources.list
```

Also post the results from this command:
```
sudo apt-get update
```

---

### Post by robinovich50 on 2020-03-19
Thank you *so much* for replying!
Here is the result for "cat /etc/apt/sources.list"
```
[COLOR=#4E9A06]**robin@robin-HP-EliteBook-8470p**[/COLOR]:[COLOR=#3465A4]**~**[/COLOR]$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017)]/ eoan main restricted
deb-src [http://mirrors.advancedhosters.com/ubuntu/](http://mirrors.advancedhosters.com/ubuntu/) eoan main restricted #Added by software-properties

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirrors.advancedhosters.com/ubuntu/](http://mirrors.advancedhosters.com/ubuntu/) eoan main restricted
deb-src [http://mirrors.advancedhosters.com/ubuntu/](http://mirrors.advancedhosters.com/ubuntu/) eoan universe restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.advancedhosters.com/ubuntu/](http://mirrors.advancedhosters.com/ubuntu/) eoan-updates main restricted
deb-src [http://mirrors.advancedhosters.com/ubuntu/](http://mirrors.advancedhosters.com/ubuntu/) eoan-updates universe main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirrors.advancedhosters.com/ubuntu/](http://mirrors.advancedhosters.com/ubuntu/) eoan universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) eoan universe
deb [http://mirrors.advancedhosters.com/ubuntu/](http://mirrors.advancedhosters.com/ubuntu/) eoan-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) eoan-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.advancedhosters.com/ubuntu/](http://mirrors.advancedhosters.com/ubuntu/) eoan multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) eoan multiverse
deb [http://mirrors.advancedhosters.com/ubuntu/](http://mirrors.advancedhosters.com/ubuntu/) eoan-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) eoan-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) eoan-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) eoan partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) eoan partner

deb [http://mirrors.advancedhosters.com/ubuntu/](http://mirrors.advancedhosters.com/ubuntu/) eoan-security main restricted
deb-src [http://mirrors.advancedhosters.com/ubuntu/](http://mirrors.advancedhosters.com/ubuntu/) eoan-security universe main restricted multiverse
deb [http://mirrors.advancedhosters.com/ubuntu/](http://mirrors.advancedhosters.com/ubuntu/) eoan-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security universe
deb [http://mirrors.advancedhosters.com/ubuntu/](http://mirrors.advancedhosters.com/ubuntu/) eoan-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) eoan main
deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) eoan main
```

Here is the result of "sudo apt-get update"

```
[COLOR=#4E9A06]**robin@robin-HP-EliteBook-8470p**[/COLOR]:[COLOR=#3465A4]**~**[/COLOR]$ sudo apt-get update
[sudo] password for robin: 
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease         
Hit:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release           
Hit:3 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan InRelease       
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) eoan InRelease             
Hit:6 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) eoan InRelease        
Get:7 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan-updates InRelease [97.5 kB]
Ign:8 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) eoan InRelease
Hit:9 [https://repo.nordvpn.com/deb/nordvpn/debian](https://repo.nordvpn.com/deb/nordvpn/debian) stable InRelease   
Err:10 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) eoan Release 
  404  Not Found [IP: 91.189.95.83 80]
Get:11 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan-security InRelease [97.5 kB]
Get:12 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan-updates/main Sources [81.5 kB]
Get:13 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan-updates/main amd64 Packages [237 kB]
Get:14 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan-updates/main i386 Packages [183 kB]
Get:15 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan-updates/main Translation-en [89.7 kB]
Get:16 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan-updates/main amd64 DEP-11 Metadata [73.0 kB]
Get:17 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan-updates/main DEP-11 48x48 Icons [9,943 B]
Get:18 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan-updates/main DEP-11 64x64 Icons [15.1 kB]
Get:19 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan-updates/universe amd64 Packages [136 kB]
Get:20 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan-updates/universe i386 Packages [130 kB]
Get:21 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan-updates/universe Translation-en [63.9 kB]
Get:22 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan-updates/universe amd64 DEP-11 Metadata [27.7 kB]
Get:23 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan-updates/universe DEP-11 48x48 Icons [18.5 kB]
Get:24 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan-updates/universe DEP-11 64x64 Icons [37.2 kB]
Get:25 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan-security/main amd64 DEP-11 Metadata [204 B]
Get:26 [http://mirrors.advancedhosters.com/ubuntu](http://mirrors.advancedhosters.com/ubuntu) eoan-security/universe amd64 DEP-11 Metadata [1,668 B]
Reading package lists... Done                                        
W: Target Sources (restricted/source/Sources) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:7
E: The repository 'http://ppa.launchpad.net/wine/wine-builds/ubuntu eoan Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Sources (restricted/source/Sources) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:7
```

Respectfully, 
Robin

---

### Post by Bashing-om on 2020-03-19
robinovich50; Hello -

As the first responder is presently offline, allow me.

In the file /etc/apt/sources.list;
1) duplicated line 2 by line 7, 
Remove line2 "  deb-src [http://mirrors.advancedhosters.com/ubuntu/](http://mirrors.advancedhosters.com/ubuntu/) eoan main restricted #Added by software-properties" as line 7 is the more complete, though it too lacks the main repo for the repository access. Better yet, if you have no need of any source code comment out all the "deb-src" calls in the file,

2)  [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) eoan : Has not caught up with the new release.
See: [http://ppa.launchpad.net/wine/wine-builds/ubuntu/dists/](http://ppa.launchpad.net/wine/wine-builds/ubuntu/dists/)
that eoan is not listed as supported.
Comment out this source call also. It is doubtful that the PPA maintainers will go to the trouble to support a short term ( 9 months) release. 

[INDENT]my bit to try and help
[/INDENT]

---

### Post by robinovich50 on 2020-03-20
Thank you for your help! I tinkered with some junk and now it works. I feel pretty smart (for asking for help, lol). Thanks everyone, Robin

---

### Post by Bashing-om on 2020-03-20
robinovich50 - :D

Ya done good work -

If this matter is now concluded to your satisfaction, then

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

