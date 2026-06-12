---
title: "repository indexes"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by accodata on 2008-09-28
Hi AllI install ubuntu  8.4.1 (Heron) but now when I go to use Synaptic or the upgrade manager I get this message, 

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

Please help me fix this. Or should I start the install all over again?

Many thanks

Tracey

---

### Post by Partyboi2 on 2008-09-29
You can go to Software Sources (System>Admin>Software Sources) and on the first tab untick the cdrom box under "installable from cd-rom/dvd" and close Software Sources and try again.

---

### Post by MJMON62 on 2008-10-11
sudo apt-cdrom add 

         If the cd is already in the drive just hit enter.:)   Took me 3 days but finally got it!!   What a great OS!!

---

### Post by amelie on 2008-11-15
Hello, guys! 
I've got the same problem as you, accodata, many thanks to the helpers,  but I don't seem to get the solution :) 
In Software resourses I don't have the chekbox under cd-rom, and MJMON62 why should I do this thing with the cd-rom, it doesn't make sense for me - i don't need any install from a cd :confused:

---

### Post by Partyboi2 on 2008-11-16
> **amelie said:**
> Hello, guys! 
I've got the same problem as you, accodata, many thanks to the helpers,  but I don't seem to get the solution :) 
In Software resourses I don't have the chekbox under cd-rom, and MJMON62 why should I do this thing with the cd-rom, it doesn't make sense for me - i don't need any install from a cd :confused:
Can you open a terminal (Applications>Accessories>Terminal) and type
```
cat /etc/apt/sources.list
```then copy and paste the output back here.

---

### Post by amelie on 2008-11-16
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080319)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by Partyboi2 on 2008-11-16
> **amelie said:**
> deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080319)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://bg.archive.ubuntu.com/ubuntu/](http://bg.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
open a terminal and type
```
gksu gedit /etc/apt/sources.list
``` then when the file open put a # infront of the cdrom line like so
```
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080319)]/ hardy main restricted
[COLOR=Red]#[/COLOR] deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080319)]/ hardy main restricted
``` then save the changes and back in the terminal
```
sudo apt-get update
```

---

### Post by ingalex on 2008-11-17
[Here]("http://www.ingalex.helloweb.eu//index.php?option=com_content&task=view&id=142&Itemid=1") you can find a custom sources.list generator. [Here]("http://www.ingalex.helloweb.eu//index.php?option=com_content&task=view&id=129&Itemid=1") you can find my full sources.list in text-version and debian-version that i update daily. If you install debian version when I update sources.list e you update all list of packets that are in repositories by apt (sudo apt-get update) or by synaptic or by other package manager, you download autamically install my sources.list updated from my repository. I hope to be helpful. Bye Bye

---

### Post by amelie on 2008-11-20
thank you guys, you're always so helpful in this forum! 
wish you the best!
amelie

---

