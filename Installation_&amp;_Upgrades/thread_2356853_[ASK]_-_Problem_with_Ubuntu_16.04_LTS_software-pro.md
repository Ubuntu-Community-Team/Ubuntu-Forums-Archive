---
title: "[ASK] - Problem with Ubuntu 16.04 LTS software-properties-gtk"
date: 2017-03-27
forum: Installation &amp; Upgrades
---

### Post by eginugraha on 2017-03-27
Hi all,
I'm new with ubuntu. and i have a problem when open software & update.
i have dialog message with error software-properties-gtk. i have search to google and at this forum.
And result is changed file ubuntu.info

but error still appearing and i cannot open software & update.

thanks, i hope someone can help me.. i'm new ubuntu user, so i confused..hahaha

---

### Post by deadflowr on 2017-03-27
I think the ubuntu.info refers to the
*/usr/share/python-apt/templates/Ubuntu.info* file.

Not sure what changed file means.
You might try to pastebin the file, as posting it here might not be the best choice, as the file is pretty hefty.
[Pastebinit on Ubuntu]("https://help.ubuntu.com/community/Pastebinit")
I'd recommend running a quick 
```
sudo apt update
sudo apt upgrade
```
to get the system to the current updated state.
For starters.

---

### Post by eginugraha on 2017-03-27
yes sir, 
i changed [I]/usr/share/python-apt/templates/Ubuntu.info file.

[/I]i'm using Ubuntu 16.04 LTS Xenial-Xerus.

i changed to

```

ChangelogURI: http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog


Suite: trusty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 14.04 'Trusty Tahr'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues


Suite: trusty
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 14.04 'Trusty Tahr'


Suite: trusty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*14.04
MatchURI: cdrom:\[Ubuntu.*14.04
Description: Cdrom with Ubuntu 14.04 'Trusty Tahr'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright


Suite: trusty
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.


Suite: trusty
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.


Suite: trusty-security
ParentSuite: trusty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates


Suite: trusty-security
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates


Suite: trusty-updates
ParentSuite: trusty
RepositoryType: deb
Description: Recommended updates


Suite: trusty-updates
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates


Suite: trusty-proposed
ParentSuite: trusty
RepositoryType: deb
Description: Pre-released updates


Suite: trusty-proposed
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates


Suite: trusty-backports
ParentSuite: trusty
RepositoryType: deb
Description: Unsupported updates


Suite: trusty-backports
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates

```

---

### Post by deadflowr on 2017-03-27
Why make those changes?

---

### Post by eginugraha on 2017-03-27
i think, when i try to install katoolin (kali tools). Kali tools automatically changes some files like .bashrc, issue, issue.net, os-release, etc..
so i try to change it manually, because i think when i type sudo apt-get update that command execute with wrong source to kali source.. hahhaa

i'm sorry my english so bad and im new with linux sir..

---

