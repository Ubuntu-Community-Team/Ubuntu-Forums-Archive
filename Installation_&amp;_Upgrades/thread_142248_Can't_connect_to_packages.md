---
title: "Can't connect to packages??"
date: 2006-03-10
forum: Installation &amp; Upgrades
---

### Post by Cysman on 2006-03-10
Hi all, I ran apt-get update and got this:


kenoutten@ubuntuhome:~$ sudo apt-get update
Get:1 [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release.gpg [65B]
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Get:2 [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release [702B]
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Hit [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Hit [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Get:3 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Fetched 708B in 14s (50B/s)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg)  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz)  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz)  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/source/Sources.gz)  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/source/Sources.gz)  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Reading package lists... Done
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
kenoutten@ubuntuhome:~$


How do I fix this?

---

### Post by linear on 2006-03-10
Sounds like the packages.freecontrib.org server was overloaded or not accepting connections for some other reason. You could always edit sources.list to comment out or remove that repository.

---

