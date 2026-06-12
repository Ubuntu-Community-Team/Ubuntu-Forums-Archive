---
title: "upgrading, reposiory error"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by Insomniac20k on 2008-05-20
I'm trying to upgrade from ubuntu 6.10 to ubuntu 8 on my laptop using the update manager. I haven't used the laptop in quite a while but have to now due to desktop breakage. When I checked for updates, it showed a lot and installed them fine then when I went to check for updates, it gave me this error:
> 
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/edgy/free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/edgy/free/source/Sources.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/source/Sources.gz:) 302 Found


So then I clicked the upgrade button, which tells me ubuntu 7 is available, and it tries to download files then gives me this error:

Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

> Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/source/Sources.gz) 302 Found


Obviously my network is fine (I am online here afterall) so I'm wondering if the repo links changed? I checked in synaptic and the repositories are checked.
 
Any help would be greatly appreciated. :popcorn:

---

### Post by forestpixie on 2008-05-20
Before you do the upgrade - disable all the 3rd party repos.

---

