---
title: "update-manager 12.10"
date: 2012-12-07
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2012-12-07
After upgrade to 12.10 I cannot update anymore. I tried even the main server, but still it complains:

> W:Failed to fetch [http://linux.dropbox.com/ubuntu/dists/quantal/main/source/Sources](http://linux.dropbox.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 199.47.216.171 80]
, W:Failed to fetch [http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-amd64/Packages](http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 199.47.216.171 80]
, W:Failed to fetch [http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 199.47.216.171 80]
, W:Failed to fetch [http://ppa.launchpad.net/dajhorn/skype-call-recorder/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/dajhorn/skype-call-recorder/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/dajhorn/skype-call-recorder/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/dajhorn/skype-call-recorder/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/dajhorn/skype-call-recorder/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/dajhorn/skype-call-recorder/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/freetuxtv/freetuxtv/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/freetuxtv/freetuxtv/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/freetuxtv/freetuxtv/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/freetuxtv/freetuxtv/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/freetuxtv/freetuxtv/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/freetuxtv/freetuxtv/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/gnac-team/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/gnac-team/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/gnac-team/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/gnac-team/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/gnac-team/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/gnac-team/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/happyaron/amule-dlp/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/happyaron/amule-dlp/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/happyaron/amule-dlp/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/happyaron/amule-dlp/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/happyaron/amule-dlp/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/happyaron/amule-dlp/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/kazam-team/stable-series/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/kazam-team/stable-series/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/kazam-team/stable-series/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/kazam-team/stable-series/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/kazam-team/stable-series/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/kazam-team/stable-series/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/mizuno-as/gimp-painter/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/mizuno-as/gimp-painter/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/mizuno-as/gimp-painter/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/mizuno-as/gimp-painter/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/mizuno-as/gimp-painter/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/mizuno-as/gimp-painter/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/telepathy/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/telepathy/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/telepathy/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/telepathy/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.95.83 80]
, W:Failed to fetch [http://ppa.launchpad.net/telepathy/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/telepathy/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.95.83 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.


My /etc/apt/sources.list looks like:
> # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal main restricted
deb-src [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal-updates main restricted
deb-src [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal universe
deb-src [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal universe
deb [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal-updates universe
deb-src [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal multiverse
deb-src [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal multiverse
deb [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal-updates multiverse
deb-src [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal-backports main restricted universe multiverse
deb-src [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal-backports main restricted universe multiverse

deb [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal-security main restricted
deb-src [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal-security main restricted
deb [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal-security universe
deb-src [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal-security universe
deb [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal-security multiverse
deb-src [http://ubuntu.cs.nctu.edu.tw/ubuntu/](http://ubuntu.cs.nctu.edu.tw/ubuntu/) quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
#deb [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free # disabled on upgrade to quantal
#deb-src [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free # disabled on upgrade to quantal
#deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) natty main # disabled on upgrade to quantal
#deb-src [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) natty main # disabled on upgrade to quantal
#deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free # disabled on upgrade to quantal
#deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) quantal main # disabled on upgrade to quantal
#deb-src [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) quantal main # disabled on upgrade to quantal
# deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free
# deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free


How to fix?

---

### Post by grahammechanical on 2012-12-07
I suggest that you go to System Settings>Software Sources and start removing those PPAs and other sources that are causing problems.

You can record the addresses in case you wish to re-instate them. It could be that the software installed through those PPAs has not been updated. Or the links are broken.

I see at least 2 PPAs that were installed for Natty. Some PPAs are used to install software but not to update software. This causes problems with updating.

In my opinion and not based upon any scientific evidence the risk of an upgrade failing is increased when the upgrade is not going from one default install to another.

Regards.

---

### Post by ELMIT on 2012-12-07
there is exactly my problem, I can not spot a single one. You even find two!

---

### Post by arpanaut on 2012-12-07
If you have installed those ppa's properly they will be in /etc/apt/sources.list.d  You can edit by hand or get to "Software Sources" either through software Center>Edit>Software Sources, under Other Software, or through Synaptic; Settings>Repositories, Other Sources from there.

You can disable the ppa's or edit to a previous releases' version, works sometimes, sometimes not.
HTH

---

### Post by ELMIT on 2012-12-07
Thanks that fixed it, ... I was only working on the /etc/apt/sources.list


Now the update-manager is gone!!!
When I call it from a terminal I get:
$ update-manager
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.

How to fix this and how do I get the update-manager back as an icon?

---

### Post by arpanaut on 2012-12-07
That's strange???  
Try ```
sudo apt-get update && sudo apt-get upgrade
```If there packages being held back try ```
sudo apt-get dist-upgrade
```watch out that there aren't packages that apt wants to remove.

If that doesn't correct things try ```
sudo apt-get install --reinstall update-manager
``` Report back any problems or error messages.
Did any of those ppa's have to do with update-manager or font configuration?

---

### Post by ELMIT on 2012-12-07
There used to be a menu entry under the Setting icon on the desktop for the update-manager, but it is not anymore there.
I can only call it from the command line.

I entered all you said, without any errors.

I don't know if any of the ppa deals with the fonts.

---

