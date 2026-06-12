---
title: "Unable to upgrade from 19.04 to 19.10"
date: 2019-12-10
forum: Installation &amp; Upgrades
---

### Post by mcsheffrey on 2019-12-10
When trying to upgrade from software updater I get a message : "A problem occurred during the update. This is usually some sort of network problem, check network connectivity and retry".
Everything looks fine in the network. 
Tried running the upgrade from terminal and these are the results:
~ ] $sudo do-release-upgrade -c -d
[sudo] password for roy: 
Checking for a new Ubuntu release
Upgrades to the development release are only 
available from the latest supported release.
[~ ] $

Any suggestions.

---

### Post by Bashing-om on 2019-12-10
mcsheffrey; Hello

The -d switch is (D)evelopment. 19.10 is no longer in development; try the command to release upgrade with no switches,
Please advise of results. 


[INDENT]my bit to try and help
[/INDENT]

---

### Post by mcsheffrey on 2019-12-10
Ok, re-ran the upgrade from terminal and got the same error:

Error during update 


A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 




Restoring original system state

There is something that it doesn't like... Everything else is working fine, network wise.

---

### Post by Bashing-om on 2019-12-10
mcsheffrey; Hummm ...

A source issue - PPA ?

Show us -between code tags to maintain formatting:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

[INDENT]gots to be a reason
[/INDENT]

---

### Post by mcsheffrey on 2019-12-10
Here's the output:

```
$cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 17.10 _Artful Aardvark_ - Release amd64 (20171018)]/ artful main restricted
     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) disco main restricted
     6	# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) artful main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) disco-updates main restricted
    11	# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) artful-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) disco universe
    17	# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) artful universe
    18	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) disco-updates universe
    19	# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) artful-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) disco multiverse
    27	# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) artful multiverse
    28	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) disco-updates multiverse
    29	# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) artful-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) disco-backports main restricted universe multiverse
    37	# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) artful-backports main restricted universe multiverse
    38	
    39	## Uncomment the following two lines to add software from Canonical's
    40	## 'partner' repository.
    41	## This software is not part of Ubuntu, but is offered by Canonical and the
    42	## respective vendors as a service to Ubuntu users.
    43	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) disco partner
    44	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful partner
    45	
    46	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) disco-security main restricted
    47	# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) artful-security main restricted
    48	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) disco-security universe
    49	# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) artful-security universe
    50	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) disco-security multiverse
    51	# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) artful-security multiverse
    52	# deb [http://repo.acestream.org/ubuntu/](http://repo.acestream.org/ubuntu/) raring main # disabled on upgrade to bionic
    53	# deb-src [http://repo.acestream.org/ubuntu/](http://repo.acestream.org/ubuntu/) raring main
    54	# deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) bionic main # disabled on upgrade to bionic
    55	# deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) artful main
    56	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) disco-proposed restricted main universe multiverse
    57	deb [https://deb.torproject.org/torproject.org](https://deb.torproject.org/torproject.org) disco main
    58	deb [https://deb.torproject.org/torproject.org](https://deb.torproject.org/torproject.org) disco main
    59	deb [https://deb.torproject.org/torproject.org](https://deb.torproject.org/torproject.org) disco main
    60	deb [https://deb.torproject.org/torproject.org](https://deb.torproject.org/torproject.org) disco main
    61	deb [https://deb.torproject.org/torproject.org](https://deb.torproject.org/torproject.org) disco main
[~ ] $

and[~ ] $tail -v -n +1 /etc/apt/sources.list.d/*==> /etc/apt/sources.list.d/alexlarsson-ubuntu-flatpak-disco.list <==


==> /etc/apt/sources.list.d/alexlarsson-ubuntu-flatpak-disco.list.save <==


==> /etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-artful.list <==
# deb [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) bionic main # disabled on upgrade to bionic
# deb-src [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) artful main


==> /etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-artful.list.distUpgrade <==
# deb [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) bionic main # disabled on upgrade to bionic
# deb-src [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) artful main


==> /etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-artful.list.save <==
# deb [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) bionic main # disabled on upgrade to bionic
# deb-src [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) artful main


==> /etc/apt/sources.list.d/gezakovacs-ubuntu-ppa-cosmic.list <==


==> /etc/apt/sources.list.d/gezakovacs-ubuntu-ppa-cosmic.list.save <==


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


==> /etc/apt/sources.list.d/ivideon.list <==
# deb [http://packages.ivideon.com/ubuntu](http://packages.ivideon.com/ubuntu) stable non-free # disabled on upgrade to bionic


==> /etc/apt/sources.list.d/ivideon.list.distUpgrade <==
# deb [http://packages.ivideon.com/ubuntu](http://packages.ivideon.com/ubuntu) stable non-free # disabled on upgrade to bionic


==> /etc/apt/sources.list.d/ivideon.list.save <==
# deb [http://packages.ivideon.com/ubuntu](http://packages.ivideon.com/ubuntu) stable non-free # disabled on upgrade to bionic


==> /etc/apt/sources.list.d/opera-beta.list <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


# deb [https://deb.opera.com/opera-beta/](https://deb.opera.com/opera-beta/) stable non-free #Opera Browser (final releases) disabled on upgrade to bionic


==> /etc/apt/sources.list.d/opera-beta.list.distUpgrade <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


# deb [https://deb.opera.com/opera-beta/](https://deb.opera.com/opera-beta/) stable non-free #Opera Browser (final releases) disabled on upgrade to bionic


==> /etc/apt/sources.list.d/opera-beta.list.save <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


# deb [https://deb.opera.com/opera-beta/](https://deb.opera.com/opera-beta/) stable non-free #Opera Browser (final releases) disabled on upgrade to bionic


==> /etc/apt/sources.list.d/opera.list <==
deb [http://deb.opera.com/opera-stable/](http://deb.opera.com/opera-stable/) stable non-free


==> /etc/apt/sources.list.d/opera.list.distUpgrade <==
deb [http://deb.opera.com/opera-stable/](http://deb.opera.com/opera-stable/) stable non-free


==> /etc/apt/sources.list.d/opera.list.save <==
deb [http://deb.opera.com/opera-stable/](http://deb.opera.com/opera-stable/) stable non-free


==> /etc/apt/sources.list.d/opera-stable.list <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


# deb [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases) disabled on upgrade to bionic


==> /etc/apt/sources.list.d/opera-stable.list.distUpgrade <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


# deb [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases) disabled on upgrade to bionic


==> /etc/apt/sources.list.d/opera-stable.list.save <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


# deb [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases) disabled on upgrade to bionic


==> /etc/apt/sources.list.d/otto-kesselgulasch-ubuntu-gimp-artful.list <==
# deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) bionic main # disabled on upgrade to bionic
# deb-src [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) artful main


==> /etc/apt/sources.list.d/otto-kesselgulasch-ubuntu-gimp-artful.list.distUpgrade <==
# deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) bionic main # disabled on upgrade to bionic
# deb-src [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) artful main


==> /etc/apt/sources.list.d/otto-kesselgulasch-ubuntu-gimp-artful.list.save <==
# deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) bionic main # disabled on upgrade to bionic
# deb-src [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) artful main


==> /etc/apt/sources.list.d/teamviewer.list <==
###   TeamViewer DEB repository list


### NOTE: Manual changes to this file
###        - prevent it from being updated by TeamViewer package updates
###        - will be lost after using the 'teamviewer repo' command
###       The original file can be restored with this command:
###       cp /opt/teamviewer/tv_bin/script/teamviewer.list /etc/apt/sources.list.d/teamviewer.list
###       which has the same effect as 'teamviewer repo default'


### NOTE: It is preferred to use the following commands to edit this file:
###       teamviewer repo                - show current repository configuration
###       teamviewer repo default        - restore default configuration
###       teamviewer repo disable        - disable the repository
###       teamviewer repo main [stable]  - make all TeamViewer packages available (default)
###       teamviewer repo tv13 [stable]  - make TeamViewer 13 packages available
###                             stable     omit preview and beta releases




### Choose stable main to receive updates for TeamViewer 13 and upcoming major releases
### Choose preview main to receive early updates for TeamViewer 13 and to receive major beta releases


### Choose stable tv13 to receive updates for TeamViewer 13
### Choose preview tv13 to receive early updates for TeamViewer 13


# deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable main # disabled on upgrade to bionic
# deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) preview main # disabled on upgrade to bionic


# deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable tv13
# deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) preview tv13


==> /etc/apt/sources.list.d/teamviewer.list.distUpgrade <==
###   TeamViewer DEB repository list


### NOTE: Manual changes to this file
###        - prevent it from being updated by TeamViewer package updates
###        - will be lost after using the 'teamviewer repo' command
###       The original file can be restored with this command:
###       cp /opt/teamviewer/tv_bin/script/teamviewer.list /etc/apt/sources.list.d/teamviewer.list
###       which has the same effect as 'teamviewer repo default'


### NOTE: It is preferred to use the following commands to edit this file:
###       teamviewer repo                - show current repository configuration
###       teamviewer repo default        - restore default configuration
###       teamviewer repo disable        - disable the repository
###       teamviewer repo main [stable]  - make all TeamViewer packages available (default)
###       teamviewer repo tv13 [stable]  - make TeamViewer 13 packages available
###                             stable     omit preview and beta releases




### Choose stable main to receive updates for TeamViewer 13 and upcoming major releases
### Choose preview main to receive early updates for TeamViewer 13 and to receive major beta releases


### Choose stable tv13 to receive updates for TeamViewer 13
### Choose preview tv13 to receive early updates for TeamViewer 13


# deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable main # disabled on upgrade to bionic
# deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) preview main # disabled on upgrade to bionic


# deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable tv13
# deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) preview tv13


==> /etc/apt/sources.list.d/teamviewer.list.dpkg-dist <==
###   TeamViewer DEB repository list


### NOTE: Manual changes to this file
###        - prevent it from being updated by TeamViewer package updates
###        - will be lost after using the 'teamviewer repo' command
###       The original file can be restored with this command:
###       cp /opt/teamviewer/tv_bin/script/teamviewer.list /etc/apt/sources.list.d/teamviewer.list
###       which has the same effect as 'teamviewer repo default'


### NOTE: It is preferred to use the following commands to edit this file:
###       teamviewer repo                - show current repository configuration
###       teamviewer repo default        - restore default configuration
###       teamviewer repo disable        - disable the repository
###       teamviewer repo stable         - make all regular TeamViewer packages available (default)
###       teamviewer repo preview        - additionally, make feature preview packages available
###       teamviewer repo development    - additionally, make the latest development packages available




deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable main


# deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) preview main
# deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) development main


==> /etc/apt/sources.list.d/teamviewer.list.save <==
###   TeamViewer DEB repository list


### NOTE: Manual changes to this file
###        - prevent it from being updated by TeamViewer package updates
###        - will be lost after using the 'teamviewer repo' command
###       The original file can be restored with this command:
###       cp /opt/teamviewer/tv_bin/script/teamviewer.list /etc/apt/sources.list.d/teamviewer.list
###       which has the same effect as 'teamviewer repo default'


### NOTE: It is preferred to use the following commands to edit this file:
###       teamviewer repo                - show current repository configuration
###       teamviewer repo default        - restore default configuration
###       teamviewer repo disable        - disable the repository
###       teamviewer repo main [stable]  - make all TeamViewer packages available (default)
###       teamviewer repo tv13 [stable]  - make TeamViewer 13 packages available
###                             stable     omit preview and beta releases




### Choose stable main to receive updates for TeamViewer 13 and upcoming major releases
### Choose preview main to receive early updates for TeamViewer 13 and to receive major beta releases


### Choose stable tv13 to receive updates for TeamViewer 13
### Choose preview tv13 to receive early updates for TeamViewer 13


# deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable main # disabled on upgrade to bionic
# deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) preview main # disabled on upgrade to bionic


# deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable tv13
# deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) preview tv13


==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-artful.list <==
# deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) cosmic main # disabled on upgrade to bionic disabled on upgrade to cosmic
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) artful main
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) artful main


==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-artful.list.distUpgrade <==
# deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) cosmic main # disabled on upgrade to bionic disabled on upgrade to cosmic
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) artful main
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) artful main


==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-artful.list.save <==
# deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) cosmic main # disabled on upgrade to bionic disabled on upgrade to cosmic
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) artful main
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) artful main


==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-bionic.list <==
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) bionic main


==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-bionic.list.distUpgrade <==
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) bionic main


==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-bionic.list.save <==
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) bionic main


==> /etc/apt/sources.list.d/ubuntu-wine-ubuntu-ppa-bionic.list <==


==> /etc/apt/sources.list.d/ubuntu-wine-ubuntu-ppa-bionic.list.save <==


==> /etc/apt/sources.list.d/vikoadi-ubuntu-ppa-cosmic.list <==


==> /etc/apt/sources.list.d/vikoadi-ubuntu-ppa-cosmic.list.save <==


==> /etc/apt/sources.list.d/virtualbox.list <==
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) disco contrib


==> /etc/apt/sources.list.d/virtualbox.list.distUpgrade <==
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) disco contrib


==> /etc/apt/sources.list.d/webupd8team-ubuntu-tor-browser-artful.list <==
# deb [http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu](http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu) bionic main # disabled on upgrade to bionic
# deb-src [http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu](http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu) artful main


==> /etc/apt/sources.list.d/webupd8team-ubuntu-tor-browser-artful.list.distUpgrade <==
# deb [http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu](http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu) bionic main # disabled on upgrade to bionic
# deb-src [http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu](http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu) artful main


==> /etc/apt/sources.list.d/webupd8team-ubuntu-tor-browser-artful.list.save <==
# deb [http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu](http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu) bionic main # disabled on upgrade to bionic
# deb-src [http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu](http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu) artful main


==> /etc/apt/sources.list.d/wine-ubuntu-test-builds-cosmic.list <==


==> /etc/apt/sources.list.d/wine-ubuntu-test-builds-cosmic.list.save <==


==> /etc/apt/sources.list.d/wine-ubuntu-wine-builds-cosmic.list <==


==> /etc/apt/sources.list.d/wine-ubuntu-wine-builds-cosmic.list.save <==
[~ ] $
```

---

### Post by Bashing-om on 2019-12-10
mcsheffrey; welp ----

/etc/apt/sources.list:
lines 57 - 61 are duplicates, remove them.

/etc/apt/sources.list.d/*:
I know nothing of teamviewer, however I can not get the link to complete. Disable this source " deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable main"

Now try again
```

sudo apt update
sudo apt upgrade

```

[INDENT]how now brown cow ?
[/INDENT]

---

### Post by mcsheffrey on 2019-12-10
I can't find where I can remove the teamviewer PPA, under "other software" in softrware update it isn't ticked off.  
Help pls.  Tks Roy

---

### Post by Bashing-om on 2019-12-10
mcsheffrey; sure :)

In the 3rd party file etc/apt/sources.list.d/

I did miss-direct you - the directory (teamviewer.list.dpkg-dist) will not be parsed in any event. I see that on the 3rd look :)
> 
 ==> /etc/apt/sources.list.d/teamviewer.list.dpkg-dist <==
### TeamViewer DEB repository list


### NOTE: Manual changes to this file
### - prevent it from being updated by TeamViewer package updates
### - will be lost after using the 'teamviewer repo' command
### The original file can be restored with this command:
### cp /opt/teamviewer/tv_bin/script/teamviewer.list /etc/apt/sources.list.d/teamviewer.list
### which has the same effect as 'teamviewer repo default'


### NOTE: It is preferred to use the following commands to edit this file:
### teamviewer repo - show current repository configuration
### teamviewer repo default - restore default configuration
### teamviewer repo disable - disable the repository
### teamviewer repo stable - make all regular TeamViewer packages available (default)
### teamviewer repo preview - additionally, make feature preview packages available
### teamviewer repo development - additionally, make the latest development packages available




deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable main


# deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) preview main
# deb [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) development main



does the upgrade run clean ?

[INDENT]easy to miss[/INDENT]

---

### Post by mcsheffrey on 2019-12-11
Still no luck, I also removed teamviewer using "[COLOR=#383838][FONT=-apple-system]sudo apt-get --purge remove teamviewer", and nothing. No sure what else to try, welcome any other ideas. Thanks.[/FONT][/COLOR]

---

### Post by ubfan1 on 2019-12-11
I was surprised to see the claim that manually added PPAs get disabled upon upgrades (except for a few problems like graphics-drivers, etc). Nevertheless, try manually disabling them, then try an update/upgrade. I see another later thread with a problem like this too.

---

### Post by mcsheffrey on 2019-12-11
Ok, I disabled all  the added PPa's and the upgrade worked. Thank you very much for all your help, much appreciated. Roy

---

### Post by mcsheffrey on 2019-12-12
Removed the added PPAs and then everything worked. Thank you very much for your help, much appreciated.  Roy

---

### Post by Bashing-om on 2019-12-12
mcsheffrey; Great !

A relief that all worked out :)

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]all's well that ends well
[/INDENT]

---

