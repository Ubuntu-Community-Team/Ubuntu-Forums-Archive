---
title: "software-properties-gui crash , lsb_release says Intrepid, Ubuntu.info has Hardy stuf"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by harijay on 2009-11-18
I am running Ubuntu Hardy Heron on a 64 bit system.

hari@hj-ubuntu41:~$ uname -a
Linux hj-ubuntu41 2.6.24-25-generic #1 SMP Tue Oct 20 06:49:12 UTC 2009 x86_64 GNU/Linux

My problem stems from an inability to run the 

"sudo software-properties-gtk"

I get the error reported before
"    "Error: could not find a distribution template")
aptsources.distro.NoDistroTemplateException"

My Ubuntu.info located at /usr/share/python-apt/templates/Ubuntu.info
does not have any of the Intrepid packages in it. It only has Hardy packages.

However my lsb_release -a says

hari@hj-ubuntu41:~$ lsb_release -a

"No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid"


How do I fix the problem and run the software-properties-gtk .

I am attaching my sources.list and  the Ubuntu.info to the bottom of this email. I am very sorry , my numerous bug report and email thread reading attempts have not helped me understand how I got into this situation in the first place.

I want to add a key for some ppa repositories for the xbmc package. The method requires me to add the keys using the software-properties-GUI

Thanks a lot for your help

Hari

########Unbuntu.info########
hari@hj-ubuntu41:~$ more /usr/share/python-apt/templates/Ubuntu.info
ChangelogURI: [http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/change](http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/change)
log

Suite: hardy
RepositoryType: deb
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-powerpc: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-powerpc: ports.ubuntu.com|archive.ubuntu.com
MirrorsFile-amd64: /usr/share/python-apt/templates/Ubuntu.mirrors
MirrorsFile-i386: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 8.04 'Hardy Heron'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: hardy
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*8.04
Description: Cdrom with Ubuntu 8.04 'Hardy Heron'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: hardy-security
ParentSuite: hardy
RepositoryType: deb
BaseURI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-powerpc: [http://ports.ubuntu.com/](http://ports.ubuntu.com/)
MatchURI-powerpc: ports.ubuntu.com/ubuntu
Description: Important security updates

Suite: hardy-updates
ParentSuite: hardy
RepositoryType: deb
Description: Recommended updates

Suite: hardy-proposed
ParentSuite: hardy
RepositoryType: deb
Description: Pre-released updates

Suite: hardy-backports
ParentSuite: hardy
RepositoryType: deb
Description: Unsupported updates


Suite: gutsy
RepositoryType: deb
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 7.10 'Gutsy Gibbon'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: gutsy
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*7.10
Description: Cdrom with Ubuntu 7.10 'Gutsy Gibbon'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: gutsy-security
ParentSuite: gutsy
RepositoryType: deb
BaseURI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: gutsy-updates
ParentSuite: gutsy
RepositoryType: deb
Description: Recommended updates

Suite: gutsy-proposed
ParentSuite: gutsy
RepositoryType: deb
Description: Pre-released updates

Suite: gutsy-backports
ParentSuite: gutsy
RepositoryType: deb
Description: Unsupported updates


Suite: feisty
RepositoryType: deb
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 7.04 'Feisty Fawn'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: feisty
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*7.04
Description: Cdrom with Ubuntu 7.04 'Feisty Fawn'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: feisty-security
ParentSuite: feisty
RepositoryType: deb
BaseURI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: feisty-updates
ParentSuite: feisty
RepositoryType: deb
Description: Recommended updates

Suite: feisty-proposed
ParentSuite: feisty
RepositoryType: deb
Description: Pre-released updates

Suite: feisty-backports
ParentSuite: feisty
RepositoryType: deb
Description: Unsupported updates

Suite: edgy
RepositoryType: deb
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 6.10 'Edgy Eft'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: edgy
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*6.10
Description: Cdrom with Ubuntu 6.10 'Edgy Eft'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: edgy-security
ParentSuite: edgy
RepositoryType: deb
BaseURI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: edgy-updates
ParentSuite: edgy
RepositoryType: deb
Description: Recommended updates

Suite: edgy-proposed
ParentSuite: edgy
RepositoryType: deb
Description: Pre-released updates

Suite: edgy-backports
ParentSuite: edgy
RepositoryType: deb
Description: Unsupported updates

Suite: dapper
RepositoryType: deb
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 6.06 LTS 'Dapper Drake'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained (universe)
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices 
Component: multiverse
CompDescription: Restricted software (Multiverse)
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: dapper
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*6.06
Description: Cdrom with Ubuntu 6.06 LTS 'Dapper Drake'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: dapper-security
ParentSuite: dapper
RepositoryType: deb
BaseURI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: dapper-updates
ParentSuite: dapper
RepositoryType: deb
Description: Recommended updates

Suite: dapper-proposed
ParentSuite: dapper
RepositoryType: deb
Description: Pre-released updates

Suite: dapper-backports
ParentSuite: dapper
RepositoryType: deb
Description: Unsupported updates

Suite: breezy
RepositoryType: deb
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 5.10 'Breezy Badger'
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: breezy
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*5.10
Description: Cdrom with Ubuntu 5.10 'Breezy Badger'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: breezy-security
ParentSuite: breezy
RepositoryType: deb
BaseURI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Ubuntu 5.10 Security Updates

Suite: breezy-updates
ParentSuite: breezy
RepositoryType: deb
Description: Ubuntu 5.10 Updates

Suite: breezy-backports
ParentSuite: breezy
RepositoryType: deb
Description: Ubuntu 5.10 Backports

Suite: hoary
RepositoryType: deb
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 5.04 'Hoary Hedgehog'
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: hoary
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*5.04
Description: Cdrom with Ubuntu 5.04 'Hoary Hedgehog'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: hoary-security
ParentSuite: hoary
RepositoryType: deb
BaseURI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Ubuntu 5.04 Security Updates

Suite: hoary-updates
ParentSuite: hoary
RepositoryType: deb
Description: Ubuntu 5.04 Updates

Suite: hoary-backports
ParentSuite: hoary
RepositoryType: deb
Description: Ubuntu 5.04 Backports

Suite: warty
RepositoryType: deb
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu
Description: Ubuntu 4.10 'Warty Warthog'
Component: main
CompDescription: No longer officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: warty
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*4.10
Description: Cdrom with Ubuntu 4.10 'Warty Warthog'
Available: False
Component: main
CompDescription: No longer officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: warty-security
ParentSuite: warty
RepositoryType: deb
BaseURI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Ubuntu 4.10 Security Updates

Suite: warty-updates
ParentSuite: warty
RepositoryType: deb
Description: Ubuntu 4.10 Updates

Suite: warty-backports
ParentSuite: warty
RepositoryType: deb
Description: Ubuntu 4.10 Backports

#########################################################################
/etc/apt/sources.list

#########################################################################'
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

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
deb [http://www.mendeley.com/repositories/xUbuntu_8.04](http://www.mendeley.com/repositories/xUbuntu_8.04) /
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main 

deb [http://ppa.launchpad.net/team-xbmc/hardy-ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/hardy-ppa/ubuntu) hardy main 
deb-src [http://ppa.launchpad.net/team-xbmc/hardy-ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/hardy-ppa/ubuntu) hardy main 

deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) hardy main 
deb-src [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) hardy main

---

