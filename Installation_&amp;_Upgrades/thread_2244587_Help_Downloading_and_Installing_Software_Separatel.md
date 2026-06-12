---
title: "Help Downloading and Installing Software Separately"
date: 2014-09-17
forum: Installation &amp; Upgrades
---

### Post by AwaitingUserInput on 2014-09-17
My home internet connection has very low bandwidth, and I have a monthly bandwidth cap that if I go over it, they start charging me extra money, so I try to minimize bandwidth-intensive operations.

For installing and upgrading software, I would like to take a laptop to a place with broadband, download the upgrades and new software to a USB drive, then go back home and install them on my desktop. I would also like to still get notices of available updates at home and save them to a list so I know what to download when I have a better connection. Can this be done?

I scanned through the man page of apt-get and found a couple references to downloading packages without installing them, but didn't see anything about installing packages that are stored locally. Is it as simple as using ```
apt-get download (packagename)
```? Then will it give me .deb packages that I can go home and just double click on?

Questions:
1) How to download now software from the repositories for installation on a different machine later?
2) How to download software updates for installation on a different machine later?
3) How do I save a list of software that needs updating?
4) How do I install updates that I downloaded to a USB drive?

Thank you!

---

### Post by slickymaster on 2014-09-17
The tool [apt-offline]("https://help.ubuntu.com/community/InstallingSoftware#Use_apt-offline") is available to help keep your computer up to date even if it cannot be kept connected. There are multiple steps involved in the process of doing this. With a USB flash drive available to you, this can be managed.

_Please refer to:_
[apt-offline homepage]("http://apt-offline.alioth.debian.org/")
[apt-offline upgrade howto]("http://www.debian-administration.org/article/Offline_Package_Management_for_APT")
[apt-offline install howto]("http://ubuntuforums.org/showpost.php?p=10198406&postcount=5")

---

### Post by AwaitingUserInput on 2014-09-17
I've been checking out the links you sent and reading man pages for apt-offline and this looks like exactly what I need. THANK YOU!

---

### Post by slickymaster on 2014-09-17
You're welcome. I'm glad it's a working solution for you.

Happy *buntuing.

---

### Post by AwaitingUserInput on 2014-09-25
If anyone finds this, I had to patch apt-offline to get it to work properly. Description is here: [http://ubuntuforums.org/showthread.php?t=2245325](http://ubuntuforums.org/showthread.php?t=2245325)

I notice that there's a new version of apt-offline that was released about a week ago, but that has not made it into the Ubuntu repositories yet, so once that happens, maybe this patch will not be needed. Until then the link above should help.

---

