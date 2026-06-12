---
title: "[SOLVED] 302 error: Failed to fetch"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by liskiewicz on 2008-12-02
Hello,

I cannot get rid of 302 error while trying to find some updates. Due to that I cannot update ubuntu to 8.10 as well. This is my /etc/apt/sources.list

```
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse


# deb [http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu) hardy main

```

I've tried with different other versions of that file downloaded from ubuntu manual or forum. I've tried with empty sources.list as well. Still 302 error occurs.

This is what I get after 
```
sudo apt-get clean
sudo apt-get update
```

```
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
  302 Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
  302 Found
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz)  302 Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz)  302 Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Pumalite on 2008-12-02
Try: 
sudo apt-get dist-upgrade

---

### Post by liskiewicz on 2008-12-02
Thanks for reply.

I've tried, but nothing changed...

---

### Post by Pumalite on 2008-12-02
Do you have a good connection to the Internet?

---

### Post by Kevbert on 2008-12-02
Can you successfully browse to any of the failing web addresses ?
It may be a problem with the web server. Open up Software Sources and try changing the server. A http 302 error is that the software sources have been temporarily moved.  Try updating again with the new server and if this fails try this in terminal:
```
cd /var/lib/dpkg
sudo mv status status-bad
sudo cp status-old status
sudo apt-get update
```
This will generate a new package list.

---

### Post by liskiewicz on 2008-12-02
Connection is ok in the sense that I can open these addresses in firefox and see long text file. I have tried with different servers in System-Administration-Software Sources-Download From without any change. New package list did not help as well. I'm confused...

---

### Post by Kevbert on 2008-12-02
How are you accessing the web? via a college/university server? Have they changed the proxy settings?
I've had a dig around and found this:
```
sudo apt-get install ubuntu-base -f
sudo apt-get install ubuntu-desktop -f
sudo apt-get dist-upgrade -f
```
It seems that the 302 error has only ever been fixed by doing this (once). There seems to be a few (old) open posts on the problem and the odd bug report. If this fails please post back again and we'll try something else.

---

### Post by liskiewicz on 2008-12-02
wowoooooo!!!

I've checked the website of my network provider, and found information that there actually is some proxy. I just did not know about it because it was automatically detected by all programs. After setting it in /etc/bash.bashrc 302 problem disappeared.

But I still cannot upgrade to 8.10. When I press button "upgrade" I am immediately getting error "Could not download the release notes". What could be the reason of that now?

---

### Post by Pumalite on 2008-12-02
Have your OS fully updated and remove all third parties from your /etc/apt/sources.list before attempting an upgrade.

---

### Post by Kevbert on 2008-12-02
You're updating from 8.04 to 8.10. In Software Sources under the Updates tab 'Normal Releases' should be selected under Release Upgrade.  If this is already set what do you get if you use the following in terminal ?
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by liskiewicz on 2008-12-03
I finally decided to update system from cd and now it's fine. I know it's not most elegant way, but it worked. I've learned something and next upgrade to 9.04 would be done by the network.

After setting this proxy, upgrade etc. system is up-to-date and everything is fine\\:D/

I was thinking that I have no proxy since firefox was automaticly detecting it, and no problem occured.

Thanks guys for help!

---

### Post by Randall on 2009-12-03
Hi all,

None of the above ended up working for me. What did work was for me to change the server that I download from, then change it back again. So in the System->Administration menu, choose Software Sources. Then on the "Ubuntu software" tab, change the server in the "download from" dropdown box. Close and get all the packages to update, then change it back again and get the updates.

---

