---
title: "[SOLVED] Can't upgrade anything?"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by icanrule on 2007-12-28
I Installed Ubuntu for the first time and am pretty new to linux.  I have been a computer user for more then 10 years though.  I'm having some troubles trying to add/remove programs through Add/Remove Programs or Synaptic Package Manager.

When I try to install basic programs like Amarok or Quanta Plus they fail saying "The list of applications is not availabe".  Did you notice the lack of an "l"? :)  Then when I view the comments it says "The (insert program name here) can not be installed on your computer type (i386).  Either the application requires special hardware features or the vendor decided to not support your computer type.

I also can't install the nvidia drivers either through the Restricted Driver Manager or by downloading directly from their website.  I think somehow these problems are related but I could be mistaken.

I am running a relatively new Toshiba P100 T2300 laptop with 1.5 gigs of ram.  It's about 15 months old.  It can't be possible that I can't install these devices?  I'm actually a little worried about the message above saying i386. It may be possible that I installed the wrong version of Ubuntu?  

Maybe someone can offer some help.  I have no idea what to do or where to begin.

---

### Post by struggling on 2007-12-28
I think that any flavor of ubuntu may be the wrong distribution.

At lease two days ago I posted on the same problem. I think it is a problem in the repositories.
No response and they are still broken.

How useful is he OS if we can't install the needed packages?

---

### Post by Partyboi2 on 2007-12-28
Check your sources.list is correct, If unsure then  post your source.list
In a terminal (Applications.Accessories>Terminal)
```
cat /etc/apt/sources.list
```

---

### Post by icanrule on 2007-12-28
Here are the results when I do that command.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restrictedwor

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

I don't actually know what any of this means.  If it helps I also just downloaded this version of Ubunt from their website and through it onto a DVD.  I chose the Desktop Addition (Ubuntu 7.10 - Supported to 2009) and then chose the type of computer as (Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)).

I wasn't sure if I should have chosen "64bit AMD and Intel computers" as the computer type.  It's worded very strangely.  I do have a an Intel computer but I think it means 64bit Intel computer which I do not have.  It might have been better to word that as "64bit AMD and 64bit Intel Computers" if they really meant they were both going to be 64bit so that Naive people like me could understand it a little better

---

### Post by icanrule on 2007-12-28
Now that I think of it when I was first installing the service I got an error at about 88% through the installation.  I can't remember the exact wording but it mentioned that it could download the updates.  I just figured that it meant that I hadn't set-up the wireless yet and I would be able to do them when I configured my wireless connection.

---

### Post by taurus on 2007-12-28
It just means that the only repo you have to install stuff from is your CD.  Therefore, you need to enable more repos if you want to install other apps.  Click System -> Administration -> Synaptic Package Manager -> Settings -> Repositories.  Now, put a check mark in front of all of them _except_ the last one, Sources code.  Also, uncheck the CDROM option at the bottom window to comment it out so it won't keep asking you to insert the CD into the drive.  Click close and Refresh.  

Now, you should be able to install whatever you want either from synaptic, Add/Remove, or from a terminal.  Remember, you need to close down synaptic if you plan to use Add/Remove.

---

### Post by icanrule on 2007-12-28
I can't believe how simple that was and quick.  It all seems to be working now.  Thanks peoples of Linux.

---

### Post by struggling on 2007-12-28
I tried enabling the repositories and get;

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)



I get the same message for the Main Server and for the Server for United States.

---

### Post by taurus on 2007-12-28
I just ran "sudo apt-get update" again on my machine and didn't have any problem accessing those repos.  What does your /etc/apt/sources.list look like anyway?

```
cat /etc/apt/sources.list
```

---

### Post by struggling on 2007-12-28
#
# deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

# deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted web

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted web

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse web

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted web
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse
#AUTOMATIX REPOS END

---

### Post by struggling on 2007-12-28
michael@xubuntu:~$ sudo apt-get update
[sudo] password for michael:
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Translation-en_US
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/web Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/web Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/web Translation-en_US
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/web Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/restricted Packages
Fetched 7B in 2s (3B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by taurus on 2007-12-28
Well, I can give you a hint but I am out since you have automatix in there and I don't want to deal with it.

Look in System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and change the Download from: to the Main server.

---

### Post by struggling on 2007-12-28
I get the same thing on the main server.

---

### Post by Partyboi2 on 2007-12-28
I think automatix is causing your problems. To find out open "Software Sources" (System>Admin>Software Sources) Click on the 3rd tab and untick the automatix box(es) then close "Software Sources" then try again.
If it works, then you know what the problem is.

---

### Post by Pumalite on 2007-12-28
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)
[http://ubuntuforums.org/announcement.php?f=13/](http://ubuntuforums.org/announcement.php?f=13/)
[http://ubuntuforums.org/showthread.php?t=519872](http://ubuntuforums.org/showthread.php?t=519872)
[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

### Post by struggling on 2007-12-29
> **Partyboi2 said:**
> I think automatix is causing your problems. To find out open "Software Sources" (System>Admin>Software Sources) Click on the 3rd tab and untick the automatix box(es) then close "Software Sources" then try again.
If it works, then you know what the problem is.

I got the same thing before I added automatix.

Will take it out and try again.

---

### Post by struggling on 2007-12-29
Did a complete removal of automatix and there is no change.

I am beginning to think the answer is a clean install,
of a different distribution.

---

### Post by Partyboi2 on 2007-12-29
You could save your current source.list and try a clean source.list and see what happens.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```A new source.list from here.
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
And replace the contents of /etc/apt/sources.list with the generated one
```
gksudo gedit /etc/apt/sources.list
```then
```
sudo apt-get update
```

---

### Post by struggling on 2007-12-30
I'll give that a try.

Even if I do go away from Ubuntu for a while I keep coming back and trying again. It is just that I have limited time to study and learn the internals to fix problems.

---

### Post by struggling on 2007-12-30
I'm not completely sure why but that did get my package management working.

Thanks!

I did end up using kate vs gedit as this is a KDE desktop.

---

### Post by Partyboi2 on 2007-12-30
Glad to hear that your problem is sorted. :)

---

