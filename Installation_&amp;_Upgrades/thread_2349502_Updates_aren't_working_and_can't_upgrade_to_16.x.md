---
title: "Updates aren't working and can't upgrade to 16.x"
date: 2017-01-15
forum: Installation &amp; Upgrades
---

### Post by chaz72 on 2017-01-15
Hey all. I'm fairly new to Ubuntu. I've used from time to time over the years and about a year ago I decided I needed to learn due to the nature of my job, so I run Ubuntu natively now on my laptop. Everything has been working great, GNS3, VMWare workstation, etc, but now all the sudden I can't do updates, nor upgrade to the latest release of Ubuntu. I'm currently running 14.04 I believe. Can anyone help me out here? When I run sudo apt-get update I get the below. I've tried sudo apt-get clean, apt-get autoclean, apt-get upgrade, and none are working.

When running apt-get update:

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/InRelease)  Unable to find expected entry 'restricted/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease)  Unable to find expected entry 'universe/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://ppa.launchpad.net/gns3/ppa/ubuntu/dists/trusty/InRelease](http://ppa.launchpad.net/gns3/ppa/ubuntu/dists/trusty/InRelease)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://ppa.launchpad.net/numix/ppa/ubuntu/dists/trusty/InRelease](http://ppa.launchpad.net/numix/ppa/ubuntu/dists/trusty/InRelease)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release](http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/Release](http://extras.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/trusty/Release](http://archive.canonical.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'partner/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Error after trying to upgrade to 16.x:

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Unable to find expected entry 'main/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-proposed/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-proposed/InRelease)  Unable to find expected entry 'restricted/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  Unable to find expected entry 'universe/binary-9386/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Note: I've made no changes to my laptop.

Also, I am unable to run GNS3 now. GNS3 keeps giving me the message that it can't connect to the local server, local server being my laptop. Thoughts? 

Thanks!

Chaz.

---

### Post by oldfred on 2017-01-15
Duplicate closed.
See
[https://ubuntuforums.org/showthread.php?t=2349500](https://ubuntuforums.org/showthread.php?t=2349500)

---

