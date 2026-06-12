---
title: "Unlisted dependency in bcmwl-kernel-source?"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by zodiac123 on 2010-11-05
Hello, I recently installed Ubuntu 10.10, dual-booting with Windows 7, on my Acer Aspire 5820TG through a liveUSB installer. However the drivers for my wireless card (a Broadcom BCM43225) was not installed. I followed the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access) after manually downloading the files bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb and dkms_2.1.1.2-3ubuntu1_all.deb from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) using Windows 7 and copying the files from the hard drive. dkms was listed as a dependency for bcmwl-kernel-source. I could install dkms but not bcmwl. After running sudo dpkg -i bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb from the command line the error message said "patch: command not found". After installing patch_2.6-2ubuntu1_amd64 manually, bcmwl-kernel-sources installed correctly.

How come patch isn't listed as a dependency for any of the packages? Also why doesn't the ubuntu software center GUI (the one that pops up if I double-click the deb file) show the output of dpkg (which I assume it uses) when an error occurs?

---

### Post by tgm4883 on 2010-11-05
Perhaps it's listed as a recommends? Sounds more like a bug though. You should file a bug in Launchpad

---

