---
title: "can't open software sources in jaunty BETA"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jayanramesh on 2009-04-07
Dear pals,
After upgraded from intrepid 64 bit to jaunty BETA I can't open software sources from "System > administration > Software sources" and there appears "No Indicators"at status bar also.Could any buddy to help me to solve this?.

Thank you.

---

### Post by cariboo on 2009-04-07
Can you open /etc/apt/sources.list using gedit? Press Alt-F2 and type:

```
gksu gedit /etc/apt/sources.list
```

What happens when you try to open System-->Administration-->Synaptic Package Manager?

Have you tried in an Applications-->Accessories-->Terminal:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Jim

---

### Post by jayanramesh on 2009-04-07
Dear Cariboo907,
I can open Synaptic package manager without any problem. Yes, I can open source list by using gedit and I 've got the result as 

"# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# deb [http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu) intrepid main
# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free

# deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
# deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) intrepid cairo-dock

deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Beta amd64 (20090324)]/ jaunty main restricted"

2.After using this code"sudo apt-get update && sudo apt-get dist-upgrade" at terminal I've got this"Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta amd64 (20090324) jaunty/main Translation-en_IN
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Beta amd64 (20090324) jaunty/restricted Translation-en_IN
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gstreamer0.10-plugins-good libcaca0
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded."

---

