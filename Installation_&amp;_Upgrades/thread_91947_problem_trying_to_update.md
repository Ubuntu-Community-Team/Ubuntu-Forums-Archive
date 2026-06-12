---
title: "problem trying to update ???"
date: 2005-11-18
forum: Installation &amp; Upgrades
---

### Post by jmejedi on 2005-11-18
Here is what I have for my sources.list (located in /etc/apt/):

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
## Uncomment the following two lines to fetch updated software from the network
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

Now, my questions:
I notice that when I try: sudo apt-get update , I get the following errors:

Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  Could not resolve 'security.ubuntu.com'
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  Could not resolve 'security.ubuntu.com'
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  Could not resolve 'security.ubuntu.com'
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  Could not resolve 'security.ubuntu.com'
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
  Could not resolve 'security.ubuntu.com'
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
  Could not resolve 'security.ubuntu.com'
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


Is this common ??? I am connect to the internet (I can ssh, I can surf the net, etc...)
Also, is there any other stuff that I should include in my "sources.list" file ??? I have a Dell 700m box.

Sorry about the long post, and Thank you for your time,

JME


P.S. Also, I usually get this when I am at home; with my ubuntu laptop plugged into my Windows home network (using McAffee Anti-virus, Firewall, etc... on all my Windows pc's)

---

### Post by Black Moon on 2005-11-18
I encountered a similar problem once when using sudo apt-get update. I then tried using update manager and was able to retrieve the needed updates. Since then I haven't had problems getting updates either way.

---

### Post by yesplease on 2005-11-18
Aysui made this: [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

Edit: that should be Aysiu.

---

