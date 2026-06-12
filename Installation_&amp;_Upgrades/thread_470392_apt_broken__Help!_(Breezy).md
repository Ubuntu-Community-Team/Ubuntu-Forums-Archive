---
title: "apt broken?  Help! (Breezy)"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by mattotoole on 2007-06-10
I've been trying to install some software, but apt can't seem to find it.  What do I do next?  Here are the error messages I'm getting:

xxx@xxxxxx:~$sudo apt-get install bluefish
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  galeon mozilla www-browser weblint-perl weblint tidy
The following NEW packages will be installed:
  bluefish
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1531kB of archives.
After unpacking 6668kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  bluefish
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe bluefish 1.0.4-1ubuntu1~breezy1
  404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/b/bluefish/bluefish_1.0.4-1ubuntu1~breezy1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/b/bluefish/bluefish_1.0.4-1ubuntu1~breezy1_i386.deb)  404 Not Found [IP: 91.189.89.6 80]
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/main Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/restricted Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/universe Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/multiverse Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Then:

xxx@xxxxxx:~$sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  404 Not Found [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  404 Not Found [IP: 82.211.81.138 80]
Hit [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  404 Not Found [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  404 Not Found [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
  404 Not Found [IP: 82.211.81.138 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
  404 Not Found [IP: 82.211.81.138 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
  404 Not Found [IP: 91.189.89.8 80]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
  404 Not Found [IP: 91.189.89.8 80]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/main Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages
  404 Not Found [IP: 91.189.89.8 80]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/restricted Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/universe Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/multiverse Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Sources
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Sources
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Sources
  404 Not Found [IP: 91.189.89.8 80]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/main Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/restricted Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/universe Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/multiverse Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz)  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz)  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz)  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/main/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/restricted/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/universe/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/multiverse/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/main Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/restricted Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/universe Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/multiverse Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by tgm4883 on 2007-06-10
Perhaps since breezy is so old and no longer supported the packages have been removed from there.  Perhaps an upgrade is in order.

---

### Post by Taino on 2007-06-11
Hmm, yeah i was just about to post about the same thing...

A bit of my errors...

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
  404 Not Found [IP: 91.189.89.8 80]

It was working fine a week ago or so, Is this a BIG HINT to upgrade or something? My laptop works fine with breezy and the partitions are set up for it (breezy takes up less partition room than what the newer releases use) I kinda wanted to stick with what works for me... ya kno.. breezy! :(

Anyone know anything official about this? are the update servers just down? or are breezy users suddenly on their own?

---

### Post by zvacet on 2007-06-11
I cheked that links and thay are O.K. Try with 

```
sudo aptitude update
```

or if you want to upgrade 

[https://help.ubuntu.com/community/DapperUpgrades]("https://help.ubuntu.com/community/DapperUpgrades")

---

### Post by ntnwwnet on 2007-06-11
Breezy became "unsuported" on the 13th of April. It's recommended that you upgrade.

---

### Post by mattotoole on 2007-06-11
I don't want to upgrade.  My machine "just works" with Breezy, and I don't have time to futz with trying to get everything to work with later versions.

So what's wrong with my Breezy installation now, and how do I fix it?

---

### Post by tgm4883 on 2007-06-11
> **mattotoole said:**
> I don't want to upgrade.  My machine "just works" with Breezy, and I don't have time to futz with trying to get everything to work with later versions.

So what's wrong with my Breezy installation now, and how do I fix it?

The package lists for breezy have been removed, it won't work.  Take a look here [http://security.ubuntu.com/ubuntu/dists/](http://security.ubuntu.com/ubuntu/dists/)  These are the only distros your getting packages for from Ubuntu.

You fix it by upgrading.

---

### Post by zvacet on 2007-06-11
it will be smart to do upgrade since Breezy is not supported anymore.Just upgrade to Dapper(you don´t need to go all the way to the Feisty if you don´t want to)and you will have runing and supported OS.

---

### Post by Taino on 2007-06-11
> **tgm4883 said:**
> The package lists for breezy have been removed, it won't work.

I just updated to the latest and greatest Ubuntu Fiesty 7.04 and it takes up so much more of my partition space that it only leaves me with 367MB of space for additional applications (and i have to have additional apps this is my Dev machine after all), So i tried Xubuntu Fiesty 7.04 and its great, its smaller and leaves me 998MB almost a gig of space for additional apps, Its just what i needed so ah Xubuntu using i will go, and man is it faster too. 

Repartitioning really wasnt an easy option on this machine, its a Dev machine and i have it setup in a very complex arrangement, it would be a major headache to repartition it, the easy solution was a distro that fit like Ubuntu Breezy 5.10 did and Xubuntu Fiesty 7.04 fits the need real good.

Thanks all... :)

---

### Post by Téragone on 2007-06-23
> **zvacet said:**
> it will be smart to do upgrade since Breezy is not supported anymore.Just upgrade to Dapper(you don´t need to go all the way to the Feisty if you don´t want to)and you will have runing and supported OS.

Supported but not working. I tried Dapper and Edgy, the 3D driver for ATI is not working 100%. Now If i try Feisty and it don't work. Not sure I will be able to fallback to Breezy.

:(

---

### Post by tgm4883 on 2007-06-23
> **Téragone said:**
> Supported but not working. I tried Dapper and Edgy, the 3D driver for ATI is not working 100%. Now If i try Feisty and it don't work. Not sure I will be able to fallback to Breezy.

:(

Doesn't sound like Breezy is working either.  Have you tried Dapper or Edgy recently?  I assume the the ATI drivers have improved since Breezy.  Also Feisty does work.  Either that or all 5 of my systems are very special because Feisty works on all of them.  Then again, I buy known working quality hardware, not cheap generic knock off crap.

---

### Post by Téragone on 2007-06-23
> **tgm4883 said:**
> Doesn't sound like Breezy is working either.  Have you tried Dapper or Edgy recently?  I assume the the ATI drivers have improved since Breezy.  Also Feisty does work.  Either that or all 5 of my systems are very special because Feisty works on all of them.

I don't have any problem with Breezy. Even with the ATI 3D driver at 1920x1200.

Maybe, I will try Feisty one day.

 > **tgm4883 said:**
>  Then again, I buy known working quality hardware, not cheap generic knock off crap.

I do the same.

---

### Post by pmshirey on 2007-06-23
Just upgrade to 7.04

---

