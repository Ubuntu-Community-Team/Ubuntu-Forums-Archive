---
title: "how to download files before upgrade?"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by errenay on 2008-05-03
I would like to upgrade to new (K)ubuntu 8.04. However, I sometimes experience problems with my internet connection (too slow, missing files). I wonder if there is any way to safely download all necessary files for upgrading (i.e. to hard drive) before main upgrade process? In case of apt-get there is something like "apt-get upgrade -d" which works in this way (first download, then I may use "apt-get update" if everything is OK).
I'm thinking about upgrade with alternate CD but there will be additional files to download apart from these on alternate CD. So, it is not the best way also in such case.

---

### Post by forestpixie on 2008-05-03
I would download the torrent - that will have the majority of the files needed - there have not been menu updates since the release. Which will more or less be the same as downloading all the upgrade packages.

If you download the torrent it will keep going till it's got all the files.

Once you have upgraded you can then set the update manager to download files without installing - that's how I have it set - I don't like to install until I've seen what is in the update set.

---

### Post by jacksaff on 2008-05-03
Apt doesn't start installing till all the downloading is done. If you don't get all files, it fails and prints you a message. All the files it did dl are still there though, in the cache. If you re-enter the upgrade command apt won't have to download all that stuff again.
The -d flag will prevent the installation part happening at all - apt will simply work out what it needs and download that to the cache. If you apt-get upgrade -d and then later apt-get upgrade then nothing will be downloaded and all the packages in the cache will get installed. You shouldn't need to do this.

---

