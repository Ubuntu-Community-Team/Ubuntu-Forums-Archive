---
title: "Can't install 6.10 to logical partition"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by gstool on 2006-12-01
I have an amd64 computer with one serial ata drive.  I have three primary partitions devoted to other OSs, an extended partition with  several data partitions and one ext3 OS partion, sa10, in which I installed Mint 2.0 yesterday.  I didn't care for Mint, so today I tried to install the amd64 edgy eft desktop over it.

During install, using manual partitioning, the installer wants to use my sda2 partition as / on which I have another Linux distro installed.  I specified that instead it should use sda10 as /, formatting it.  However, I get stopped with a "No Root partition" error and can't proceed.

Just to be sure it wasn't the amd64 CD, I tried the same thing with the normal edgy desktop live/install CD.  Same result.

What gives, and how can I proceed?

Thanks.  Gerry

---

### Post by rsambuca on 2006-12-01
For some reason there is a bug with the Edgy installer when trying to install into pre-existing partitions.

There is a clumsy workaround:

[http://ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://ubuntuforums.org/showpost.php?p=1700787&postcount=29)

---

